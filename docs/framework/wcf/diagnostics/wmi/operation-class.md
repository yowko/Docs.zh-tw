---
title: 作業類別
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 6b47d933dc84813532398830c92c95210208a709
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269154"
---
# <a name="operation-class"></a>作業類別

作業  
  
## <a name="syntax"></a>Syntax  
  
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

 資料類型：字串  
  
 存取類型：唯讀  
  
 要求訊息的 WS-Addressing 動作。  
  
### <a name="asyncpattern"></a>AsyncPattern  

 資料型別：布林值  
  
 存取類型：唯讀  
  
 表示 `Begin` 在服務合約中使用 [開放式/右角括弧] 和 `End` [開啟/關閉角括弧] 方法組，以非同步方式執行作業。  
  
### <a name="behaviors"></a>行為  

 資料型別：行為陣列  
  
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

 資料類型：字串  
  
 存取類型：唯讀  
  
 作業的方法簽章。  
  
### <a name="name"></a>Name  

 資料類型：字串  
  
 存取類型：唯讀  
  
 作業的名稱。  
  
### <a name="parametertypes"></a>ParameterTypes  

 資料型別：字串陣列  
  
 存取類型：唯讀  
  
 作業的參數類型。  
  
### <a name="replyaction"></a>ReplyAction  

 資料類型：字串  
  
 存取類型：唯讀  
  
 作業的回覆訊息的 SOAP 動作值。  
  
### <a name="returntype"></a>ReturnType  

 資料類型：字串  
  
 存取類型：唯讀  
  
 作業的傳回型別。  
  
## <a name="requirements"></a>規格需求  
  
|MOF|於 Servicemodel.mof 中宣告。|  
|---------|-----------------------------------|  
|命名空間|於 root\ServiceModel 中定義|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Description.OperationDescription>
