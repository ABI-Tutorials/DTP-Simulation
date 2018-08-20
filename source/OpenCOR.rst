.. _dtp_cp_sim_opencor:

Brownie points: Where do these models come from?
================================================

.. contents::

In the previous steps in this tutorial, you have explored simulations performed using mathematical models encoded in the `CellML <https://cellml.org>`_ format. CellML provides a powerful technology to encode these models in a modular and reusable manner which is easily exchangable between tools.

Task 5: explore CellML using OpenCOR
++++++++++++++++++++++++++++++++++++

In this task, we switch from MAP Client to :ref:`OpenCOR <cellml_opencor_pmr_tutorial__installation>`. The first step is to get some familarity with using OpenCOR to create models and execute simulations. This can be achieved by working through :ref:`cellml_opencor_pmr_tutorial__first_model`.

Did you notice that link at the end of that section? With a single click you are able to launch the Van der Pol oscillator in OpenCOR and immediately simulate and interact with the model.

#. How cool is that?

Task 6: find the ICC model
++++++++++++++++++++++++++

As you will have seen, using the model repository and OpenCOR it is *usually* easy to find useful models and explore them as an aid to understanding some aspect of the model or system represented by the model.

#. Take a look at :ref:`cellml_opencor_pmr_tutorial__open_existing` to learn another way to find models in the repository and load it into OpenCOR.
#. Can you find the ICC model from Task 3 in the repository? Load the ICC model into OpenCOR and see if you can reproduce the simulation behaviours you observed when exploring the simulation settings in Task 3 using the MAP Client.
#. Pretty cool that these two different tools can access the same model description and (hopefully) get the same results, right?!

Task 7: the Simulation Experiment Description Markup Language
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Once you are able to reproduce the simulations and plots from Task 3, it would be good to save the configuration of the simulation so that you are able to easily re-run the simulation experiment in a manner similar to that Van der Pol oscillator link above.

#. See :ref:`cellml_opencor_pmr_tutorial__sedml_web_lab` to learn how to achieve this.
#. Try and export a SED-ML document which reproduces the ICC simulation result you observed back in Task 3 (preferably a working instance, but getting the same errors is also verification!).
#. Share the SED-ML document with a fellow student and see if they are able to get the same result.


Task 8: explore alternate ICC models
++++++++++++++++++++++++++++++++++++

One benefit of computational physiology is that it makes it easy to explore and compare different hypotheses. The ICC model introduced in Task 3 is a model that captures one representation of the ICC electrophysiology, but there are others. To finsh off this part of the module, take a look through the repository to explore some of the other ICC models that are available. And since the ICC cells are primarily driving the contraction of the smooth muscle cells in the GI system, you might want to see if you can discover any smooth muscle cell models that might be relevant to the GI system.

