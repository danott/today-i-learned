You can use [reorder][] on an ActiveRecordRelation to replace all existing order
methods. It's super useful when merging scopes that may have imported their own
ordering that is no longer applicable.

[reorder]: http://apidock.com/rails/ActiveRecord/QueryMethods/reorder
