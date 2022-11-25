# 数据库

> You can prevent the test databases from being destroyed by using the `test --keepdb` option. This will preserve the test database between runs. If the database does not exist, it will first be created. Any migrations will also be applied in order to keep it up to date.
> As described in the previous section, if a test run is forcefully interrupted, the test database may not be destroyed. On the next run, you’ll be asked whether you want to reuse or destroy the database. Use the `test --noinput` option to suppress that prompt and automatically destroy the database. This can be useful when running tests on a continuous integration server where tests may be interrupted by a timeout, for example.
