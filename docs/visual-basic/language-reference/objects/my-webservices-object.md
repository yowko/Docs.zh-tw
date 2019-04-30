---
title: My.WebServices 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: a60f32c4f581e42f240fca55ce496776c5511ba3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050281"
---
# <a name="mywebservices-object"></a>My.WebServices 物件
提供建立及存取目前專案所參考的每個 XML Web 服務的單一執行個體的屬性。  
  
## <a name="remarks"></a>備註  
 `My.WebServices` 物件會提供目前專案所參考之每個 Web 服務的執行個體。 每個執行個體都是依需要具現化。 您可以透過 `My.WebServices` 物件的屬性來存取這些 Web 服務。 屬性名稱和屬性存取的 Web 服務名稱相同。 任何繼承自 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> 的類別都是 Web 服務。 Web 服務新增至專案的相關資訊，請參閱[存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
 `My.WebServices`物件會公開僅與目前專案相關聯的 Web 服務。 它不提供宣告參考的 Dll 中的 Web 服務的存取權。 若要存取 DLL 所提供的 Web 服務，您必須使用 Web 服務的限定的名稱，形式*DllName*。*WebServiceName*。 如需詳細資訊，請參閱 <<c0> [ 存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
 物件和其屬性不適用於 Web 應用程式。  
  
## <a name="properties"></a>屬性  
 每一個屬性的`My.WebServices`物件提供存取目前專案所參考的 Web 服務的執行個體。 屬性的名稱與相同的屬性存取，Web 服務的名稱，屬性類型是與 Web 服務的型別相同。  
  
> [!NOTE]
>  如果沒有名稱衝突，存取 Web 服務的屬性名稱是*RootNamespace*_*命名空間*\_*ServiceName*。 例如，假設名為兩個 Web 服務`Service1`。 如果上述其中一個服務是在根命名空間`WindowsApplication1`和命名空間`Namespace1`，您會使用來存取該服務`My.WebServices.WindowsApplication1_Namespace1_Service1`。  
  
 當您第一次存取其中一個`My.WebServices`物件的屬性，它會建立 Web 服務的新執行個體，並將它儲存。 後續的存取，該屬性會傳回該執行個體的 Web 服務。  
  
 您可以藉由指定 Web 服務的處置`Nothing`設為該 Web 服務的屬性。 屬性 setter 指派`Nothing`的預存值。 如果您指派任何值以外`Nothing`於屬性 setter 會擲回<xref:System.ArgumentException>例外狀況。  
  
 您可以測試的屬性是否`My.WebServices`物件會儲存使用的 Web 服務的執行個體`Is`或`IsNot`運算子。 您可以使用這些運算子，來檢查屬性的值是否為`Nothing`。  
  
> [!NOTE]
>  通常`Is`或`IsNot`操作員必須讀取要比較之屬性的值。 不過，如果屬性目前儲存`Nothing`，屬性會建立 Web 服務的新執行個體，並接著會傳回該執行個體。 不過，Visual Basic 編譯器會將屬性`My.WebServices`物件，並允許`Is`或`IsNot`運算子來檢查屬性的狀態，而不需要變更其值。  
  
## <a name="example"></a>範例  
 這個範例會呼叫`FahrenheitToCelsius`方法的`TemperatureConverter`XML Web service，並傳回結果。  
  
 [!code-vb[VbVbalrMyWebService#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyWebService/VB/Form1.vb#1)]  
  
 針對此範例正常運作，您的專案必須參考名為 Web 服務`Converter`，且該 Web 服務必須公開`ConvertTemperature`方法。 如需詳細資訊，請參閱 <<c0> [ 存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
 此程式碼無法運作的 Web 應用程式專案中。  
  
## <a name="requirements"></a>需求  
  
### <a name="availability-by-project-type"></a>專案類型的可用性  
  
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
