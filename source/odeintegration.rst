.. _dtp_cp_sim_odeintegration:

Integrating systems of differential equations
=============================================

In this tutorial we look into the integration of systems of differential equations, using example models from the domain of computational physiology. We also examine the the main control parameters that can have a significant impact on the performance and accuracy of a given method.

.. contents::
   :local: 
   :depth: 2
   :backlinks: top

.. _dtp_cp_sim_ode_integrators:

Numerical integrators
---------------------

.. _dtp_cp_sim_ode_euler:

Euler method
************

The `Euler method <http://en.wikipedia.org/wiki/Euler_method>`_ to integrate a system of ordinary differential equations is probably the most well known method, particularly popular given its simplicity. Due to its simplicity it is, however, usually not the most appropriate method to use when performing simulation experiments with complex models of biological systems. It is, however, a very useful example to use to demonstrate key concepts that apply to most numerical integration methods.

Given the initial value problem

.. math:: y'(t) = f(t, y(t)), \quad\quad y(t_0) = y_0, 
   :label: dtp_cp_sim_euler_system
   
we now want to approximate :math:`y(t)` over some interval :math:`t_0 \rightarrow t_{final}`. The Euler method approximates :math:`y(t)` by dividing the interval into a series of steps, of size :math:`h`, and stepping through the interval. One step of the Euler method from :math:`t_n` to :math:`t_{n+1} = t_n + h` is given by

.. math:: y_{n+1} = y_n + h f(t_n, y_n).
   :label: dtp_cp_sim_euler_step 

The value of :math:`y_n` is an approximation of the solution of the ODE :eq:`dtp_cp_sim_euler_system` at time :math:`t_n`: :math:`y_n \approx y(t_n)`. The Euler method proceeds through the interval in constant steps of size :math:`h` until :math:`t_n = t_{final}` and the integration is complete.

The effect of step size
+++++++++++++++++++++++

As you'd imagine, the size of :math:`h` in the Euler method is crucial to the successful application of the method. For the successful (although perhaps inaccurate) integration of a typical physiological model (see the `Physiome Repository <https://models.physiomeproject.org>`_ for a collection of examples), :math:`h` can be so small that the computational cost of performing the simulation is very high. In some cases, mathematical models may be unsuitable for integration by Euler method, regardless of how small the step size is reduced to.

In the follow task, we investigate the effect of altering the size of :math:`h` on two separate simulation experiments. The first looks at a simple mathematical model where the experiment could be replicated with pen and paper, while the second looks into the application of Euler's method to a biophysical model of cellular electrophysiology.

Task 1
~~~~~~

The following task assumes familiarity with the :ref:`virtual machine <dtp_cp_virtualmachine>`. In this task we use the trivial model:

.. math::
   :label: dtp_cp_sim_sine_model
   
   x(t) &= \mathit{sin}(t),\\
   y'(t) &= \mathit{cos}(t) \quad\mathrm{with}\quad y(0) = 0.
   
As you can see from :eq:`dtp_cp_sim_sine_model`, if correctly integrated :math:`x(t)` and :math:`y(t)` should be identical. We now use this model to demonstrate the effect of step size (:math:`h`) on simulating this model using Euler integration over the interval :math:`0 \rightarrow 2 \pi`.

1. Run MAP Client, choose :menuselection:`File --> Open` and select :file:`{HOME}/projects/mapclient-workflows/DTP-Simulation-Task1`.
2. This simple workflow should look similar to :numref:`fig_dtp_cp_sim_euler1`. The workflow is pre-configured so there is no configuration required.

.. _fig_dtp_cp_sim_euler1:

.. figure:: images/euler1.png
   :align: center
   :figwidth: 95%
   :width: 90%
   :alt: Task 1 workbench.
   
   The first Euler example as loaded. The step to configure is highlighted.
   
3. Click the :guilabel:`Execute` button and you should get a widget displayed as per :numref:`fig_dtp_cp_sim_euler2`.

.. _fig_dtp_cp_sim_euler2:

.. figure:: images/euler2.png
   :align: center
   :figwidth: 95%
   :width: 90%
   :alt: Task 1 GUI.
   
   The cool GUI.
   
4. As shown in :numref:`fig_dtp_cp_sim_euler2`, clicking the :guilabel:`simulate` button will run a simulation using the currently specified step size.

.. _dtp_cp_sim_ode_cvode:

CVODE
*****

From the `Sundials <https://computation.llnl.gov/casc/sundials/main.html>`_ suite of tools, CVODE is a solver for stiff and nonstiff ordinary differential equation (ODE) systems (initial value problem) given in explicit form :math:`y' = f(t,y)`.  