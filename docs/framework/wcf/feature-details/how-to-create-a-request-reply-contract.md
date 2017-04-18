---
title: "HOW TO：建立要求-回覆合約 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 801d90da-3d45-4284-9c9f-56c8aadb4060
caps.latest.revision: 19
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 19
---
# HOW TO：建立要求-回覆合約
要求\-回覆合約會指定一個方法以傳回回覆。回覆必須在此合約條件下進行傳送並與要求相互關聯。即便該方法未傳回任何回覆 \(在 C\# 為 `void`，在 Visual Basic 為 `Sub`\)，基礎結構還是會建立空訊息並傳送給呼叫者。若要避免傳送空的回覆訊息，請使用單向作業合約。  
  
### 建立要求\-回覆合約  
  
1.  使用您選擇的程式語言建立一個介面。  
  
2.  將 <xref:System.ServiceModel.ServiceContractAttribute> 屬性套用至該介面。  
  
3.  將 <xref:System.ServiceModel.OperationContractAttribute> 屬性套用至用戶端可能叫用的每個方法。  
  
4.  選擇性。將 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 屬性設定為 `true` 值，以免傳送空的回覆訊息。預設情況下，所有各項作業都是要求\-回覆合約。  
  
## 範例  
 下列範例針對提供 `Add` 和 `Subtract` 方法的計算機服務定義合約。`Multiply` 方法不是合約的一部分，因為它未加上 <xref:System.ServiceModel.OperationContractAttribute> 類別標示，以致無法供用戶端存取。  
  
```  
using System.ServiceModel;   
  
[ServiceContract]   
public interface ICalculator   
{   
[OperationContract]   
// It would be equivalent to write explicitly:  
// [OperationContract(IsOneWay=false)]   
int Add(int a, int b);   
  
[OperationContract]   
int Subtract(int a, int b);   
  
int Multiply(int a, int b)  
}  
```  
  
-   [!INCLUDE[crabout](../../../../includes/crabout-md.md)]如何指定作業合約的詳細資訊，請參閱 <xref:System.ServiceModel.OperationContractAttribute> 類別和 <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> 屬性。  
  
-   藉由套用 <xref:System.ServiceModel.ServiceContractAttribute> 和 <xref:System.ServiceModel.OperationContractAttribute> 屬性，部署服務時就會自動產生服務合約定義，亦即 Web 服務描述語言 \(WSDL\) 文件。只要將 `?wsdl` 附加至服務的 HTTP 基底位址，便能夠下載這份文件。例如：`http://microsoft/CalculatorService?wsdl`  
  
## 請參閱  
 <xref:System.ServiceModel.OperationContractAttribute>   
 [設計服務合約](../../../../docs/framework/wcf/designing-service-contracts.md)   
 [HOW TO：建立雙工合約](../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md)