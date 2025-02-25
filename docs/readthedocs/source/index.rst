.. meta::
   :google-site-verification: S66K6GAclKw1RroxU0Rka_2d1LZFVe27M0gRneEsIVI

=================================================
The BigDL Project
=================================================

------

---------------------------------
BigDL-LLM: low-Bit LLM library
---------------------------------
`bigdl-llm <https://github.com/intel-analytics/BigDL/tree/main/python/llm>`_ is a library for running **LLM** (large language model) on your Intel **laptop** or **GPU** using INT4 with very low latency [*]_ (for any **PyTorch** model).

.. note::

   It is built on top of the excellent work of `llama.cpp <https://github.com/ggerganov/llama.cpp>`_, `gptq <https://github.com/IST-DASLab/gptq>`_, `bitsandbytes <https://github.com/TimDettmers/bitsandbytes>`_, `qlora <https://github.com/artidoro/qlora>`_, etc.

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Latest update
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
- ``bigdl-llm`` now supports Intel Arc and Flex GPU; see the the latest GPU examples `here <https://github.com/intel-analytics/BigDL/tree/main/python/llm/example/gpu>`_.
- ``bigdl-llm`` tutorial is released `here <https://github.com/intel-analytics/bigdl-llm-tutorial>`_.
- Over 20 models have been verified on ``bigdl-llm``, including *LLaMA/LLaMA2, ChatGLM/ChatGLM2, MPT, Falcon, Dolly-v1/Dolly-v2, StarCoder, Whisper, QWen, Baichuan,* and more; see the complete list `here <https://github.com/intel-analytics/BigDL/tree/main/python/llm/README.md#verified-models>`_.


^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
``bigdl-llm`` demos
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

See the **optimized performance** of ``chatglm2-6b``, ``llama-2-13b-chat``, and ``starcoder-15.5b`` models on a 12th Gen Intel Core CPU below.

.. raw:: html
   
   <p align="center">
            <img src="https://github.com/bigdl-project/bigdl-project.github.io/blob/master/assets/chatglm2-6b.gif?raw=true" width='30%' /> <img src="https://github.com/bigdl-project/bigdl-project.github.io/blob/master/assets/llama-2-13b-chat.gif?raw=true" width='30%' /> <img src="https://github.com/bigdl-project/bigdl-project.github.io/blob/master/assets/llm-15b5.gif?raw=true" width='30%' />
            <img src="https://github.com/bigdl-project/bigdl-project.github.io/blob/master/assets/llm-models3.png?raw=true" width='76%'/>
  </p>

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
``bigdl-llm`` quickstart
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

You may install ``bigdl-llm`` as follows:

.. code-block:: console

   pip install --pre --upgrade bigdl-llm[all]

.. note::

   ``bigdl-llm`` has been tested on Python 3.9.

You can then apply INT4 optimizations to any Hugging Face *Transformers* models as follows.

.. code-block:: python

   #load Hugging Face Transformers model with INT4 optimizations
   from bigdl.llm.transformers import AutoModelForCausalLM
   model = AutoModelForCausalLM.from_pretrained('/path/to/model/', load_in_4bit=True)

   #run the optimized model
   from transformers import AutoTokenizer
   tokenizer = AutoTokenizer.from_pretrained(model_path)
   input_ids = tokenizer.encode(input_str, ...)
   output_ids = model.generate(input_ids, ...)
   output = tokenizer.batch_decode(output_ids)

**For more details, please refer to the bigdl-llm** `Readme <https://github.com/intel-analytics/BigDL/tree/main/python/llm>`_, `Tutorial <https://github.com/intel-analytics/bigdl-llm-tutorial>`_ and `API Doc <https://bigdl.readthedocs.io/en/latest/doc/PythonAPI/LLM/index.html>`_.

------

---------------------------------
Overview of the complete BigDL project
---------------------------------
`BigDL <https://github.com/intel-analytics/bigdl>`_ seamlessly scales your data analytics & AI applications from laptop to cloud, with the following libraries:

- `LLM <https://github.com/intel-analytics/BigDL/tree/main/python/llm>`_: Low-bit (INT3/INT4/INT5/INT8) large language model library for Intel CPU/GPU
- `Orca <doc/Orca/index.html>`_: Distributed Big Data & AI (TF & PyTorch) Pipeline on Spark and Ray
- `Nano <doc/Nano/index.html>`_: Transparent Acceleration of Tensorflow & PyTorch Programs on Intel CPU/GPU
- `DLlib <doc/DLlib/index.html>`_: "Equivalent of Spark MLlib" for Deep Learning
- `Chronos <doc/Chronos/index.html>`_: Scalable Time Series Analysis using AutoML
- `Friesian <doc/Friesian/index.html>`_: End-to-End Recommendation Systems
- `PPML <doc/PPML/index.html>`_: Secure Big Data and AI (with SGX Hardware Security)

------

---------------------------------
Choosing the right BigDL library
---------------------------------

.. graphviz::

    digraph BigDLDecisionTree {
        graph [pad=0.1 ranksep=0.3 tooltip=" "]
        node [color="#0171c3" shape=box fontname="Arial" fontsize=14 tooltip=" "]
        edge [tooltip=" "]
        
        Feature1 [label="Hardware Secured Big Data & AI?"]
        Feature2 [label="Python vs. Scala/Java?"]
        Feature3 [label="What type of application?"]
        Feature4 [label="Domain?"]
        
        LLM[href="https://github.com/intel-analytics/BigDL/blob/main/python/llm" target="_blank" target="_blank" style="rounded,filled" fontcolor="#ffffff" tooltip="Go to BigDL-LLM document"]
        Orca[href="../doc/Orca/index.html" target="_blank" target="_blank" style="rounded,filled" fontcolor="#ffffff" tooltip="Go to BigDL-Orca document"]
        Nano[href="../doc/Nano/index.html" target="_blank" target="_blank" style="rounded,filled" fontcolor="#ffffff" tooltip="Go to BigDL-Nano document"]
        DLlib1[label="DLlib" href="../doc/DLlib/index.html" target="_blank" style="rounded,filled" fontcolor="#ffffff" tooltip="Go to BigDL-DLlib document"]
        DLlib2[label="DLlib" href="../doc/DLlib/index.html" target="_blank" style="rounded,filled" fontcolor="#ffffff" tooltip="Go to BigDL-DLlib document"]
        Chronos[href="../doc/Chronos/index.html" target="_blank" style="rounded,filled" fontcolor="#ffffff" tooltip="Go to BigDL-Chronos document"]
        Friesian[href="../doc/Friesian/index.html" target="_blank" style="rounded,filled" fontcolor="#ffffff" tooltip="Go to BigDL-Friesian document"]
        PPML[href="../doc/PPML/index.html" target="_blank" style="rounded,filled" fontcolor="#ffffff" tooltip="Go to BigDL-PPML document"]
        
        ArrowLabel1[label="No" fontsize=12 width=0.1 height=0.1 style=filled color="#c9c9c9"]
        ArrowLabel2[label="Yes" fontsize=12 width=0.1 height=0.1 style=filled color="#c9c9c9"]
        ArrowLabel3[label="Python" fontsize=12 width=0.1 height=0.1 style=filled color="#c9c9c9"]
        ArrowLabel4[label="Scala/Java" fontsize=12 width=0.1 height=0.1 style=filled color="#c9c9c9"]
        ArrowLabel5[label="Large Language Model" fontsize=12 width=0.1 height=0.1 style=filled color="#c9c9c9"]
        ArrowLabel6[label="Big Data + \n AI (TF/PyTorch)" fontsize=12 width=0.1 height=0.1 style=filled color="#c9c9c9"]
        ArrowLabel7[label="Accelerate \n TensorFlow / PyTorch" fontsize=12 width=0.1 height=0.1 style=filled color="#c9c9c9"]
        ArrowLabel8[label="DL for Spark MLlib" fontsize=12 width=0.1 height=0.1 style=filled color="#c9c9c9"]
        ArrowLabel9[label="High Level App Framework" fontsize=12 width=0.1 height=0.1 style=filled color="#c9c9c9"]
        ArrowLabel10[label="Time Series" fontsize=12 width=0.1 height=0.1 style=filled color="#c9c9c9"]
        ArrowLabel11[label="Recommender System" fontsize=12 width=0.1 height=0.1 style=filled color="#c9c9c9"]
        
        Feature1 -> ArrowLabel1[dir=none]
        ArrowLabel1 -> Feature2
        Feature1 -> ArrowLabel2[dir=none]
        ArrowLabel2 -> PPML
        
        Feature2 -> ArrowLabel3[dir=none]
        ArrowLabel3 -> Feature3
        Feature2 -> ArrowLabel4[dir=none]
        ArrowLabel4 -> DLlib1
        
        Feature3 -> ArrowLabel5[dir=none]
        ArrowLabel5 -> LLM
        Feature3 -> ArrowLabel6[dir=none]
        ArrowLabel6 -> Orca
        Feature3 -> ArrowLabel7[dir=none]
        ArrowLabel7 -> Nano
        Feature3 -> ArrowLabel8[dir=none]
        ArrowLabel8 -> DLlib2
        Feature3 -> ArrowLabel9[dir=none]
        ArrowLabel9 -> Feature4
     
        Feature4 -> ArrowLabel10[dir=none]
        ArrowLabel10 -> Chronos
        Feature4 -> ArrowLabel11[dir=none]
        ArrowLabel11 -> Friesian
    }

------

.. [*] Performance varies by use, configuration and other factors. ``bigdl-llm`` may not optimize to the same degree for non-Intel products. Learn more at www.Intel.com/PerformanceIndex.
