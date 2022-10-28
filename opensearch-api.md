# ElasticSearch (OpenSearch) API Usage

測試環境：Postman

### Create new record
Method: POST

API Endpoint: your-domain/your-index/_doc/[(optional) your-custom-id]

Authorization: Basic Auth (username/password)

Body: 序列化的JSON Object

### Delete by SQL
Method: POST

API Endpoint: your-domain/your-index/_delete_by_query?[param]

Authorization: Basic Auth (username/password)

Url param: 
* requests_per_second=400 每秒刪除數量限制
* max_docs=2000 最多刪除檔案數量

Body: Query Object (json)
* 刪除超過90天以上的檔案

```
{
 "query": {
   "range": {
     "CreatedAt": {
       "lte": "now-90d"
      }
    }
  }
}
```

* 刪除符合條件的檔案(Uri有ReCaptcha)
```
{
    "query": {
        "match": {
            "Uri": "ReCaptcha"
        }
    }
}
```
**備註：刪除的動作會在要刪除的資料上標記為delete，等之後執行資料整理的時候才會真的從disk上刪除。(Whenever a document is deleted it doesn't immediately release space. It is just marked as delete. When small segments are merged, that is the time when elastic discard the deleted marked documents and actually delete them from disk.)

參考資料：[Does updating a doc increase the "delete" count of the index?](https://stackoverflow.com/questions/57121822/does-updating-a-doc-increase-the-delete-count-of-the-index)
