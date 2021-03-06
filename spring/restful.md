### 可以通过requestBody和responseBody标签来声明一个restful风格的接口，前提是类路径下加入了jackson的jar包，用于将json解析成对象以及将对象解析成json

## responseBody测试
```java
/**
 * restful接口风格测试
 * @param id
 * @return
 * @throws Exception
 */
@RequestMapping(value = "/getFeedbackWorkOrder/{id}", method = RequestMethod.GET, produces = "application/json; charset=utf-8")
@ResponseBody
public FeedbackWorkOrder getFeedbackWorkOrder(@PathVariable Integer id) throws Exception{
  FeedbackWorkOrder order = service.getFeedbackWorkOrderById(id);
  return order;
}
```
### 返回的格式
```json
{
  "id": 1075,
  "aid": 1,
  "sid": -4001,
  "feedbackType": "申诉",
  "productVersion": 16,
  "submitter": 112,
  "source": -12,
  "processingPhase": 3,
  "state": 2,
  "isBeBack": false,
  "isAgent": false,
  "isUrgent": false,
  "recordState": 0,
  "createTime": 1522826783000,
  "updateTime": 1522826783000,
  "link": "",
  "remark": "<p>第丝丝</p>",
  "labellings": [
    
  ],
  "orderFiles": [
    {
      "id": "AIQBCAAQAhgAIJz8kdYFKLzznvwC",
      "name": "sea-person-ocean-531062.jpeg",
      "isImg": true,
      "fileUrl": "http://1.s132d.aaadns.com/0/AIQBCAAQAhgAIJz8kdYFKLzznvwC.jpeg"
    },
    {
      "id": "AIQBCAAQAhgAIJ78kdYFKJC0178E",
      "name": "u=3875477328,2431869157&fm=27&gp=0.jpg",
      "isImg": true,
      "fileUrl": "http://1.s132d.aaadns.com/0/AIQBCAAQAhgAIJ78kdYFKJC0178E.jpg"
    }
  ],
  "logList": [
    {
      "id": 7277,
      "formId": 1075,
      "sid": 112,
      "replyId": -1,
      "time": 1522826783,
      "action": "创建了工单#1075\r\n<p>第丝丝</p>",
      "type": 10,
      "flow": 10191000,
      "processingPhase": 0,
      "orderType": 4,
      "files": null,
      "showTime": "2018-04-04 15:26:23",
      "staffName": null,
      "fileList": null,
      "showAcct": "faisco",
      "terminalShow": "faisco",
      "hasDeleteReplyBtn": false,
      "processingPhaseStr": "提交工单"
    }
  ],
  "productVersionStr": "商城基础版",
  "submitterName": "系统管理员",
  "showAcct": "faisco",
  "groupId": -4001,
  "formatRemark": "<p>第丝丝</p>",
  "resultsList": [
    "已整改",
    "已提供有效证件",
    "依然违规",
    "无法提供证件"
  ],
  "diff": 0,
  "clearTaeTime": false,
  "clearProductType": false,
  "clearResult": false,
  "clearOrderFiles": false,
  "labellingStr": "",
  "orderType": 4,
  "showProcessingPhase": "工单领取",
  "showState": "待领取",
  "staffName": "",
  "createTimeStr": "2018-04-04 15:26:23",
  "updateTimeStr": "2018-04-04 15:26:23",
  "taeTimeStr": "",
  "labellingsStr": "",
  "isInternallySubmitted": false
}
```

## requestBody测试
#### 后台接口
```java
//要和consumes搭配使用才足够严格，这样子对前端的传参要求，就是一个json字符串，然后到后台这边，将该字符串解析成java对象
@PostMapping(value="/updateFeedbackOrder",consumes="application/json; charset=utf-8")
public void updateFeedbackOrder(@RequestBody FeedbackWorkOrder order) {
  System.out.println(order);
  try {
    System.out.println(JsonUtil.objToJson(order));
  } catch (Exception e) {
    // TODO Auto-generated catch block
    e.printStackTrace();
  }
}
```
#### 前端请求
```js
function postFeedbackOrder(){
    var order = new Object();
    order.id = 10086;
    order.name = "郑泽荣";
    order.phone = "18218487622";

    $.ajax({ 
        type:"POST", 
        url:"feedbackOrder/updateFeedbackOrder", 
        dataType:"json",      
        **`contentType:"application/json",`** //该参数为必须的，呼应后台的consumes值 
        data:JSON.stringify(order), 
        success:function(data){
          console.log(data);
        } 
     }); 
}
```
#### 可以做相应的修改，进行list类型的传输
