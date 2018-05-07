---
title: My.WebServices 物件
ms.date: 07/20/2015
f1_keywords:
- My.WebServices
- My.MyProject.WebServices
helpviewer_keywords:
- My.WebServices object
ms.assetid: f188dc05-2c75-41b6-bb68-122d1c3110a2
ms.openlocfilehash: 9519638c7609b9b1d0f5e07397c46975e2696c94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="mywebservices-object"></a>My.WebServices 物件
提供建立及存取目前的專案所參考的每個 XML Web 服務的單一執行個體的屬性。  
  
## <a name="remarks"></a>備註  
 `My.WebServices` 物件會提供目前專案所參考之每個 Web 服務的執行個體。 每個執行個體都是依需要具現化。 您可以透過 `My.WebServices` 物件的屬性來存取這些 Web 服務。 屬性名稱和屬性存取的 Web 服務名稱相同。 任何繼承自 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol> 的類別都是 Web 服務。 將 Web 服務加入專案的相關資訊，請參閱[存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
 `My.WebServices`物件會公開只與目前的專案相關聯的 Web 服務。 它不會提供在被參考 Dll 中宣告的 Web 服務的存取權。 若要存取 DLL 所提供的 Web 服務，您必須在表單中使用 Web 服務中的限定的名稱*DllName*。*WebServiceName*。 如需詳細資訊，請參閱[存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
 物件和其屬性不適用於 Web 應用程式。  
  
## <a name="properties"></a>屬性  
 每一個屬性的`My.WebServices`物件提供存取目前的專案所參考的 Web 服務的執行個體。 名稱屬性的屬性存取，Web 服務的名稱相同，且屬性類型就是 Web 服務的型別相同。  
  
> [!NOTE]
>  如果沒有名稱衝突，存取 Web 服務的屬性名稱是*RootNamespace*_*命名空間*\_*ServiceName*。 例如，假設名為兩個 Web 服務`Service1`。 如果其中一個服務位於根命名空間`WindowsApplication1`和命名空間`Namespace1`，您會使用來存取該服務`My.WebServices.WindowsApplication1_Namespace1_Service1`。  
  
 當您第一次存取其中一個`My.WebServices`物件的屬性，它會建立 Web 服務的新執行個體，並將它儲存。 後續存取該屬性會傳回該執行個體的 Web 服務。  
  
 您可以藉由指派處置 Web 服務`Nothing`設為該 Web 服務的屬性。 屬性 setter 指派`Nothing`儲存值。 如果您指派以外的任何值`Nothing`於屬性 setter 會擲回<xref:System.ArgumentException>例外狀況。  
  
 您可以測試是否屬性`My.WebServices`物件會使用儲存的 Web 服務執行個體`Is`或`IsNot`運算子。 您可以使用這些運算子來檢查屬性的值是否為`Nothing`。  
  
> [!NOTE]
>  一般而言，`Is`或`IsNot`運算子具有讀取要比較之屬性的值。 不過，如果屬性目前儲存`Nothing`，屬性建立 Web 服務的新執行個體，然後傳回該執行個體。 不過，Visual Basic 編譯器會將屬性`My.WebServices`蓄意，物件，並可讓`Is`或`IsNot`運算子來檢查屬性狀態，而不會變更其值。  
  
## <a name="example"></a>範例  
 這個範例會呼叫`FahrenheitToCelsius`方法`TemperatureConverter`XML Web 服務，並傳回結果。  
  
 [!code-vb[VbVbalrMyWebService#1](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-webservices-object_1.vb)]  
  
 要讓範例能夠運作，您的專案必須參考名為 Web 服務`Converter`，並且必須公開該 Web 服務`ConvertTemperature`方法。 如需詳細資訊，請參閱[存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)。  
  
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
 <xref:System.Web.Services.Protocols.SoapHttpClientProtocol>  
 <xref:System.ArgumentException>  
 [存取應用程式 Web 服務](../../../visual-basic/developing-apps/programming/accessing-application-web-services.md)
