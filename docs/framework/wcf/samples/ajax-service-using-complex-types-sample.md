---
title: "使用複雜型別的 AJAX 服務範例 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# 使用複雜型別的 AJAX 服務範例
這個範例會示範如何使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 來建立 ASP.NET Asynchronous JavaScript 與 XML \(AJAX\) 服務，此服務會建立複雜類型的執行個體，並在服務和用戶端之間以 Javascript 物件標記法 \(JSON\) 進行傳送。您可以從 Web 瀏覽器用戶端使用 JavaScript 程式碼存取 AJAX 服務。這個範例是以[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例為基礎所建立。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 中的 AJAX 支援已針對透過 <xref:System.Web.UI.ScriptManager> 控制項來搭配 ASP.NET AJAX 使用完成最佳化。如需搭配 ASP.NET AJAX 使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的範例，請參閱 [AJAX Samples](http://msdn.microsoft.com/zh-tw/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 下列範例中的服務是沒有使用 AJAX 特定程式碼的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。因為沒有套用 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性，所以會使用預設的 HTTP 動詞命令 \("POST"\)。服務有一項 `MathResult` 作業，它會傳回名為 `DoMath` 的複雜類型。複雜類型是標準資料合約型別，其中也未包含 AJAX 特定程式碼。  
  
```  
[DataContract]  
    public class MathResult  
    {  
        [DataMember]  
        public double sum;  
        [DataMember]  
        public double difference;  
        [DataMember]  
        public double product;  
        [DataMember]  
        public double quotient;  
    }  
```  
  
 您可以在服務上使用 <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> 來建立 AJAX 端點，如基本 AJAX 服務範例所示。  
  
 用戶端網頁 ComplexTypeClientPage.aspx 會包含 ASP.NET 和 JavaScript 程式碼，以便在使用者按一下頁面上的 \[**執行計算**\] 按鈕時叫用此服務。用來叫用此服務的程式碼會建構 JSON 本文，並使用 HTTP POST 加以傳送，這種做法類似於[使用 HTTP POST 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)範例。  
  
 在服務呼叫成功後，您就可以存取在結果 JavaScript 物件上的個別資料成員 \(`sum`、`difference`、`product` 和 `quotient`\)。  
  
```  
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
  
```  
  
### 若要設定、建置及執行範例  
  
1.  請確定您已執行 [Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2.  使用[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中描述的方式建置方案 ComplexTypeAjaxService.sln。  
  
3.  瀏覽到 http:\/\/localhost\/ServiceModelSamples\/ComplexTypeClientPage.aspx \(不要使用瀏覽器從專案目錄開啟 ComplexTypeClientPage.aspx\)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## 請參閱  
 [基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)