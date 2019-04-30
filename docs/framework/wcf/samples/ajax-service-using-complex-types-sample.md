---
title: 使用複雜型別的 AJAX 服務範例
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: cde7e48d0f0c44d68266d60399ac197d322a42cc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002881"
---
# <a name="ajax-service-using-complex-types-sample"></a>使用複雜型別的 AJAX 服務範例
此範例示範如何使用 Windows Communication Foundation (WCF) 來建立 ASP.NET Asynchronous JavaScript 與 XML (AJAX) 服務會建立複雜型別的執行個體，並將它們傳送服務和用戶端做為 JavaScript Object Notation (JSON) 之間。 您可以從 Web 瀏覽器用戶端使用 JavaScript 程式碼存取 AJAX 服務。 這個範例是根據[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例。  
  
 在 WCF 中的 AJAX 支援最適合用於透過 ASP.NET AJAX<xref:System.Web.UI.ScriptManager>控制項。 使用 WCF 與 ASP.NET AJAX 的範例，請參閱[AJAX 範例](ajax.md)。  
  
> [!NOTE]
>  此範例的安裝程序與建置指示位於本主題的結尾。  
  
 下列範例中的服務是未 AJAX 特定程式碼使用 WCF 服務。 因為沒有套用 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性，所以會使用預設的 HTTP 動詞命令 ("POST")。 服務有一項 `DoMath` 作業，它會傳回名為 `MathResult` 的複雜型別。 複雜型別是標準資料合約型別，其中也未包含 AJAX 特定程式碼。  

```csharp
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
  
 用戶端網頁 ComplexTypeClientPage.aspx 會包含在使用者按一下時叫用服務的 ASP.NET 和 JavaScript 程式碼**執行計算**頁面上的按鈕。 要叫用服務的程式碼會建構 JSON 本文，並將它使用 HTTP POST，類似於傳送[使用 HTTP POST 的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)範例。  
  
 在服務呼叫成功後，您就可以存取在結果 JavaScript 物件上的個別資料成員 (`sum`、`difference`、`product` 和 `quotient`)。  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1. 請確定您已執行[Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 中所述，建置方案 ComplexTypeAjaxService.sln[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
3. 瀏覽至`http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx`（不要在瀏覽器從專案目錄開啟 ComplexTypeClientPage.aspx）。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a>另請參閱

- [基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
