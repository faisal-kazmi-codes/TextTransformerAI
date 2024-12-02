## Library

#### t5.data

`t5.data` is a package for defining `Task` objects that provide `tf.data.Dataset`s.

Each `Task` is made up of:

  * a data source
  * text preprocessor function(s)
  * a SentencePiece model
  * metric function(s)

Additionally, you may optionally provide:

  * token preprocessor function(s)
  * postprocess function(s)

The **data source** can be an arbitrary function that provides a `tf.data.Dataset`, but we also provide simpler wrappers for datasets available in [TensorFlow Datasets (TFDS)][tfds] (a `TfdsTask`) or stored as text files with one example per line (a `TextLineTask`).

The **text preprocessor** converts the examples in the source dataset into the appropriate format for a text-to-text model with fields for `inputs` and `targets`.  For example, the predefined `t5.data.preprocessors.translate` preprocessor converts inputs in the form

```py
{'de': 'Das ist gut.', 'en': 'That is good.'}
```

to the form

```py
{'inputs': 'translate German to English: Das ist gut.', 'targets': 'That is good.'}
```
