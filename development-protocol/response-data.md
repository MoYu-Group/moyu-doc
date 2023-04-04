# 接口返回值约定
MoYu 开发小组的所有接口，应遵循统一的数据格式规范，以提高我们的前后端开发效率;

现在对接口返回值做以下约定，开发时应严格遵守约定，使用框架层的统一返回值处理，禁止自定义返回值

### 统一返回值格式

```json
{
    "success": true,
    "code": "success",
    "message": "",
    "content": {
        "currentPage": 1,
        "pageSize": 10,
        "totalCount": 1,
        "totalPage": 1,
        "data": [
            {
                "id": 1
            }
        ]
    }
}

```

### 统一返回值格式说明
| 属性名     | 数据格式    | 说明                      |
|---------|---------|-------------------------|
| success | Boolean | 业务成功标识，成功：true；失败：false |
| code    | String  | 业务处理状态代码，具体要另外定义        |
| message | String  | 业务处理状态附加信息，如错误信息        |
| content | T       | 返回的业务数据                 |

#### 分页时返回的对象
| 属性名            | 数据格式      | 说明                        |
|----------------|-----------|---------------------------|
| content        | Page      | 返回的分页数据                   |
| └─ currentPage | Long      | 当前页                       |
| └─ pageSize    | Long      | 页大小                       |
| └─ totalCount  | Long      | 总记录数                      |
| └─ totalPage   | Long      | 总页数                       |
| └─ data        | `List<T>` | 分页时返回的对象列表                |
| └─└─ id        | Long      | 对象唯一标识，会作为查询、删除、更改的参数传给后端 |
