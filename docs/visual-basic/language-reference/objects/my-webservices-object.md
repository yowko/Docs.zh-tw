---
title: WebServices 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: c887f9b7c5a41c0aa02016354c46d5507b103d25
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918173"
---
# <a name="mywebservices-object"></a>My.WebServices 物件
提供屬性, 用來建立及存取目前專案所參考之每個 XML Web Service 的單一實例。  
  
## <a name="remarks"></a>備註  
 `My.WebServices` 物件會提供目前專案所參考之每個 Web 服務的執行個體。 每個執行個體都是依需要具現化。 您可以透過 `My.WebServices` 物件的屬性來存取這些 Web 服務。 屬性名稱和屬性存取的 Web 服務名稱相同。 任何繼承自 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> 的類別都是 Web 服務。 如需將 Web 服務新增至專案的詳細資訊, 請參閱[存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
 `My.WebServices`物件只會公開與目前專案相關聯的 Web 服務。 它不會提供參考 Dll 中所宣告之 Web 服務的存取權。 若要存取 DLL 提供的 Web 服務, 您必須使用 Web 服務的限定名稱, 格式為*DllName*。*WebServiceName*。 如需詳細資訊, 請參閱[存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
 Web 應用程式無法使用物件及其屬性。  
  
## <a name="properties"></a>屬性  
 `My.WebServices`物件的每個屬性都可讓您存取目前專案所參考之 Web 服務的實例。 屬性的名稱與屬性所存取之 Web 服務的名稱相同, 而且屬性類型與 Web 服務的類型相同。  
  
> [!NOTE]
> 如果發生名稱衝突, 用於存取 Web 服務的屬性名稱是*RootNamespace*_*Namespace* \_ *ServiceName*。 例如, 假設有兩個名為`Service1`的 Web 服務。 如果其中一項服務位於根命名空間`WindowsApplication1`和命名空間`Namespace1`中, 您會使用`My.WebServices.WindowsApplication1_Namespace1_Service1`來存取該服務。  
  
 當您第一次存取`My.WebServices`物件的其中一個屬性時, 它會建立新的 Web 服務實例並加以儲存。 後續存取該屬性會傳回該 Web 服務的實例。  
  
 您可以藉由指派`Nothing`給該 web 服務的屬性來處置 web 服務。 屬性 setter 會指派`Nothing`給儲存的值。 如果您將以外`Nothing`的任何值指派給屬性, setter <xref:System.ArgumentException>就會擲回例外狀況。  
  
 您可以`My.WebServices` `Is`使用or`IsNot`運算子來測試物件的屬性是否儲存 Web 服務的實例。 您可以使用這些運算子來檢查屬性的值是否為`Nothing`。  
  
> [!NOTE]
> 一般而言, `Is`或`IsNot`運算子必須讀取屬性的值, 才能執行比較。 不過, 如果屬性目前儲存`Nothing`, 則屬性會建立 Web 服務的新實例, 然後傳回該實例。 不過, Visual Basic 編譯器會特別處理`My.WebServices`物件的屬性, 並`Is`允許或`IsNot`運算子檢查屬性的狀態, 而不需要變更其值。  
  
## <a name="example"></a>範例  
 這個範例會呼叫`FahrenheitToCelsius` `TemperatureConverter` XML Web Service 的方法, 並傳回結果。  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 為了讓此範例正常執行, 您的專案必須參考名為`Converter`的 web 服務, 而且該 web 服務`ConvertTemperature`必須公開方法。 如需詳細資訊, 請參閱[存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
 這段程式碼無法在 Web 應用程式專案中運作。  
  
## <a name="requirements"></a>需求  
  
### <a name="availability-by-project-type"></a>依專案類型的可用性  
  
|專案類型|可用|  
|---|---|  
|Windows 應用程式|**是**|  
|類別庫|**是**|  
|主控台應用程式|**是**|  
|Windows 控制項程式庫|**是**|  
|Web 控制項程式庫|**是**|  
|Windows 服務|**是**|  
|網站|否|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>
- <xref:System.ArgumentException>
- [存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
