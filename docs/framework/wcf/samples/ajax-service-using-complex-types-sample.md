---
title: 使用複雜型別的 AJAX 服務範例
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: 98d33c250be31ac43eef6d76ade997a30af87090
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923685"
---
# <a name="ajax-service-using-complex-types-sample"></a>使用複雜型別的 AJAX 服務範例
這個範例會示範如何使用 Windows Communication Foundation (WCF) 來建立 ASP.NET 的非同步 JavaScript 和 XML (AJAX) 服務, 以建立複雜型別的實例, 並在服務和用戶端之間將它們當做 JavaScript 物件標記法 (JSON) 傳送。 您可以從 Web 瀏覽器用戶端使用 JavaScript 程式碼存取 AJAX 服務。 這個範例是以[基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)範例為基礎。  
  
 WCF 中的 AJAX 支援已優化, 可透過<xref:System.Web.UI.ScriptManager>控制項與 ASP.NET ajax 搭配使用。 如需搭配使用 WCF 與 ASP.NET AJAX 的範例, 請參閱[AJAX 範例](ajax.md)。  
  
> [!NOTE]
> 此範例的安裝程序與建置指示位於本主題的結尾。  
  
 下列範例中的服務是不含 AJAX 特定程式碼的 WCF 服務。 因為沒有套用 <xref:System.ServiceModel.Web.WebGetAttribute> 屬性，所以會使用預設的 HTTP 動詞命令 ("POST")。 服務有一項 `DoMath` 作業，它會傳回名為 `MathResult` 的複雜型別。 複雜型別是標準資料合約型別，其中也未包含 AJAX 特定程式碼。  

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
  
 用戶端網頁 Complextypeclientpage.aspx 會包含 ASP.NET 和 JavaScript 程式碼, 可在使用者按一下頁面上的 [**執行計算**] 按鈕時叫用服務。 用來叫用服務的程式碼會使用 HTTP POST 來建立 JSON 主體並傳送它, 類似于[使用 HTTP post 範例的 AJAX 服務](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)。  
  
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
  
1. 請確定您已[針對 Windows Communication Foundation 範例執行一次安裝程式](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
2. 如[建立 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)中所述, 建立方案 ComplexTypeAjaxService。  
  
3. 流覽至`http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx` (請勿在瀏覽器中從專案目錄開啟 complextypeclientpage.aspx 會)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在, 請移至[.NET Framework 4 的 Windows Communication Foundation (wcf) 和 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780), 以下載所有 Windows Communication Foundation (wcf) [!INCLUDE[wf1](../../../../includes/wf1-md.md)]和範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a>另請參閱

- [基本 AJAX 服務](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
