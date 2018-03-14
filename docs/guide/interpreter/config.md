<h1> Inline Interpreter configuration </h1>

`%[Interpreter name].config` is a special interpreter that allows configure interpreter properties and environment variables in each notebook. Becuase configuration can be part of notebook in this way, it gives benefits

  - Share notebook with interpreter configuration it reqruies (Reproducibility)
  - Find-grained control on interpreter configuration on notebook level.


## Usage

```
%[Interpreter name to configure].config
[Key 2]       [Value 1]         # comment
[Key 2]       [Value 2]
...
```

Note that inline configuration must run before any other normal paragraphs. So usually it will be placed on top of a notebook.

### Key

Key can not include empty space. `[A-Z_0-9]+` is threated as a environment variable, otherwise interpreter property. e.g.

 - `spark.app.name`, `python.python` - Interpreter property
 - `SPARK_HOME`, `CUSTOM_VAR` - Environment variable

### Value

Value is seprated by spaces or tabs from key. Value can include any character except for newline. For example, followings are all valid

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


