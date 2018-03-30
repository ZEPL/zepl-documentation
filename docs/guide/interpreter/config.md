<h1> Inline Interpreter configuration </h1>

`%[Interpreter name].config` is a special interpreter that allows for interpreter properties and environment variables to be configured in each notebook. This features brings additional flexibility enabling users to do, among other things:

  - Share a notebook with a custom interpreter configuration or specific environment variable the paragraphs require already set. 
  - Fine-grained control on interpreter configuration at notebook level.


## Usage

```
%[Interpreter name to configure].config
[Key 2]       [Value 1]         # comment
[Key 2]       [Value 2]
...
```

Note that inline configuration must run before any other paragraph. So it will usually be the first paragraph in the notebook.

### Key

Key can not include empty space. `[A-Z_0-9]+` is treated as a environment variable, otherwise it's considered an interpreter property. e.g.:

 - `spark.app.name`, `python.python` - Interpreter property
 - `SPARK_HOME`, `CUSTOM_VAR` - Environment variable

### Value

Value is separated by spaces or tabs from Key. Value can include any character except for newline. For example, following are all valid:

 - `100`, `true`, `/dir/path`, `spark app name`


### Example


```
%spark.config

spark.app.name           ZEPL     # override default spark app name
AWS_ACCESS_KEY_ID        ....     # AWS access key
AWS_SECRET_ACCESS_KEY    ....     # AWS secret key
```

```
%spark
val data = sc.read.text("s3a://...")
```


