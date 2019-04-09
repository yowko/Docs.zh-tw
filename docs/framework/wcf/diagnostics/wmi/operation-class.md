---
title: 作業類別
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 9696a7f026e54afacb5ccbfa8703a2ba617a9f3d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59165070"
---
# <a name="operation-class"></a>作業類別
運算  
  
## <a name="syntax"></a>語法  
  
```csharp
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a>方法  
 Operation 類別不會定義任何方法。  
  
## <a name="properties"></a>屬性  
 Operation 類別具有下列屬性：  
  
### <a name="action"></a>動作  
 資料型別：字串  
  
 存取類型：唯讀  
  
 要求訊息的 WS-Addressing 動作。  
  
### <a name="asyncpattern"></a>AsyncPattern  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 表示以非同步方式實作作業`Begin`[開啟/關閉角括號] 和`End`採用服務合約中的 [開啟/關閉角度 brackets] 方法組。  
  
### <a name="behaviors"></a>「行為」  
 資料類型：行為陣列  
  
 存取類型：唯讀  
  
 與這個作業有關聯的行為。  
  
### <a name="iscallback"></a>IsCallback  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 當作業是回呼作業時為 True。  
  
### <a name="isinitiating"></a>IsInitiating  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表方法是否實作可在伺服器上初始化工作階段的作業。  
  
### <a name="isoneway"></a>IsOneWay  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表作業是否傳回回覆訊息。  
  
### <a name="isterminating"></a>IsTerminating  
 資料型別：布林值  
  
 存取類型：唯讀  
  
 代表作業是否傳回回覆訊息。  
  
### <a name="methodsignature"></a>MethodSignature  
 資料型別：字串  
  
 存取類型：唯讀  
  
 作業的方法簽章。  
  
### <a name="name"></a>名稱  
 資料型別：字串  
  
 存取類型：唯讀  
  
 作業的名稱。  
  
### <a name="parametertypes"></a>ParameterTypes  
 資料型別：字串陣列  
  
 存取類型：唯讀  
  
 作業的參數類型。  
  
### <a name="replyaction"></a>ReplyAction  
 資料型別：字串  
  
 存取類型：唯讀  
  
 作業的回覆訊息的 SOAP 動作值。  
  
### <a name="returntype"></a>ReturnType  
 資料型別：字串  
  
 存取類型：唯讀  
  
 作業的傳回型別。  
  
## <a name="requirements"></a>需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Description.OperationDescription>
