# 世界疫情数据获取开放接口

## 写在最前面

- 此数据爬取丁香园数据，来源丁香园
- 使用时，请标注出处：丁香园&赵嘚住
- 数据仅供数据分析使用，不可商用
- 希望数据早点定格，这场人类的灾难早点过去，明天是个晴天。

## 关于数据和接口

- 提供的接口为实时数据和2020年3月24日以后的数据
- 请不要使用压测工具挑战服务器的性能，谨慎使用，大量调用将会采取封ip等措施
- 接口地址: https://covid19.zhaodeezhu.com/api
- 主要字段说明，其他字段自行理解

| 字段                  | 说明         | 示例值                     |
| --------------------- | ------------ | -------------------------- |
| provinceName          | 省份全称     | 湖北省                     |
| provinceShortName     | 身份简称     | 湖北                       |
| currentConfirmedCount | 现存确诊数量 | 800                        |
| confirmedCount        | 全部确诊数量 | 900                        |
| suspectedCount        | 疑似病例     | 0                          |
| curedCount            | 治愈数量     | 900                        |
| deadCount             | 死亡数量     | 0                          |
| cityName              | 城市名称     | 武汉                       |
| continents            | 州名         | 亚洲                       |
| provinceName          | 国家名       | 伊朗                       |
| countryShortCode      | 国家英文简称 | IRN                        |
| countryFullName       | 国家全称     | Iran (Islamic Republic of) |

## API

### 获取中国疫情数据

- **api**      **/covid19/getRealTimeChinaData**

- **method**    **GET**

- **response**

```javascript
{
  code: 200,
  message: '成功',
  data: [
    {
      // 省份
      provinceName: "湖北省"，
      // 省份简称
      provinceShortName: "湖北",
      // 现存确诊数量
      currentConfirmedCount: 5719,
      // 总确诊数量
      confirmedCount: 67800,
      // 疑似病例
      suspectedCount: 0,
      // 治愈数量
      curedCount: 58942,
      // 死亡数量
      deadCount: 3139,
      // 区号
      locationId: 420000,
      // 城市汇总
      cities: [
        {
          // 城市名
          cityName: "武汉",
          currentConfirmedCount: 5610,
          confirmedCount: 222,
          suspectedCount: 0,
          curedCount: 41891,
          deadCount: 2504,
          locationId: 420100
         }
       ]
     }
  ]
}
```

### 获取中国疫情数据汇总

- **API**      **/covid19/getRealTimeChinaCount**

- **method**    **GET**

- **response**

```javascript
{
  "code": 200,
  "data": {
    "currentConfirmedCount": 6279,
    "confirmedCount": 81416,
    "suspectedCount": 0,
    "curedCount": 71876,
    "deadCount": 3261,
    "dateTime": "2020-3-21 11:35:21"
  },
  "message": "成功了"
}
```

###获取世界疫情数据

- **API**    **/covid19/getRealTimeForeignData**

- **method**   **GET**
- **response**

```javascript
{
  code: 200,
  message: "成功",
 	data: [
    {
			"id": 1445965,
			"createTime": 1584761548000,
			"modifyTime": 1584761548000,
			"tags": "",
			"countryType": 2,
			"continents": "欧洲",
			"provinceId": "10",
			"provinceName": "意大利",
			"provinceShortName": "",
			"cityName": "",
			"currentConfirmedCount": 37860,
			"confirmedCount": 47021,
			"suspectedCount": 0,
			"curedCount": 5129,
			"deadCount": 4032,
			"comment": "",
			"sort": 0,
			"operator": "chend",
			"locationId": 965008,
			"countryShortCode": "ITA",
			"countryFullName": "Italy",
      "statisticsData": "https://file1.dxycdn.com/2020/0315/993/3402160517102843054-135.json",
			"incrVo": {
				"currentConfirmedIncr": 0,
				"confirmedIncr": 0,
				"curedIncr": 0,
				"deadIncr": 0
			}
    }
  ]
}
```

### 获取世界疫情数据汇总

- **API**     **/covid19/getRealTimeForeignCount**

- **method**    **GET**
- **response**

```javascript
{
	"code": 200,
	"data": {
		"currentConfirmedCount": 6279,
		"confirmedCount": 81416,
		"suspectedCount": 0,
		"curedCount": 71876,
		"deadCount": 3261,
		"dateTime": "2020-3-21 11:35:21"
	},
	"message": "成功了"
}
```

### 获取历史数据

- **API**    **/covid19/getHistoryData**
- **method**    **GET**
- **requset query**

| 字段         | 说明                             | 必须 | 示例       |
| ------------ | -------------------------------- | :--: | ---------- |
| locationType | 地区类型，china中国，foreign国外 |  Y   | china      |
| curdDate     | 数据日期                         |  Y   | 2020-03-24 |

- **response**

```javascript
{
  code: 200,
	data: [
    {
      "id": 440,
      "provinceName": "湖北省",
      "provinceShortName": "湖北",
      "locationId": 420100,
      "comment": "",
      "cityName": "武汉",
      "currentConfirmedCount": 4268,
      "confirmedCount": 50006,
      "suspectedCount": 0,
      "curedCount": 43214,
      "deadCount": 2524,
      "curdDate": "2020-03-23T16:00:00.000Z"
    }
  ]
}
```

### 获取历史数据汇总

- **API**      **/covid19/getHistoryTypeCount**

- **method**    **GET**
- **request query**       同上

- **response**

```javascript
{
  code: 200,
  data: [
    {
      "currentConfirmedCount": 4740,
      "confirmedCount": 81180,
      "suspectedCount": 1,
      "curedCount": 73163,
      "deadCount": 3277,
      "curdDate": "2020-03-23T16:00:00.000Z"
    }
  ]
}
```

### 获取今日汇总和与昨日的差值

- **API**    **/covid19/getDateDifferenceCount**
- **method**    **GET**
- **request query** 

| 字段         | 说明                             | 必须 | 示例    |
| ------------ | -------------------------------- | ---- | ------- |
| locationType | 地区类型，china中国，foreign国外 | Y    | foreign |

- **response**

```javascript
{
  code: 200,
  data: {
    // 昨天的汇总数据
    "yesDate": {
      "currentConfirmedCount": 4740,
      "confirmedCount": 81180,
      "suspectedCount": 1,
      "curedCount": 73163,
      "deadCount": 3277,
      "curdDate": "2020-03-23T16:00:00.000Z"
    },
    // 今天的汇总数据
    "toData": {
       "currentConfirmedCount": 4813,
       "confirmedCount": 81896,
       "suspectedCount": 78,
       "curedCount": 73796,
       "deadCount": 3287,
       "dateTime": "2020-3-25 19:07:47"
    },
    // 差值
    "currentConfirmedCountDiff": 73,
    "confirmedCountDiff": 716,
    "suspectedCountDiff": 77,
    "curedCountDiff": 633,
    "deadCountDiff": 10
  }
}
```

