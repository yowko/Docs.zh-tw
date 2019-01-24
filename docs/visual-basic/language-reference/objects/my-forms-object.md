---
title: My.Forms 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 17042f60eb27c41640ef5d8c927c7acc5bc73183
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712614"
---
# <a name="myforms-object"></a>My.Forms 物件
提供存取目前專案中宣告的每個 Windows form 的執行個體的屬性。  
  
## <a name="remarks"></a>備註  
 `My.Forms`物件會提供目前專案中的每個表單的執行個體。 屬性存取表單的名稱相同的屬性名稱。   
  
 您可以存取所提供的表單`My.Forms`物件使用的格式，但是不限定的名稱。 屬性名稱是表單的類型名稱相同，因為這可讓您存取表單，如同它已有的預設執行個體。 例如，`My.Forms.Form1.Show` 等於 `Form1.Show`。  
  
 `My.Forms`物件會公開僅將目前的專案相關聯的表單。 它不提供宣告之參考的 Dll 中表單的存取。 若要存取 DLL 所提供的表單，您必須使用表單時，寫成的限定的名稱*DllName*。*FormName*。  
  
 您可以使用<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>屬性來取得應用程式的所有開啟表單的集合。  
  
 物件和其屬性是僅適用於 Windows 應用程式。  
  
## <a name="properties"></a>屬性  
 每一個屬性的`My.Forms`物件提供存取目前專案中撰寫表單的執行個體。 屬性的名稱與相同的屬性存取時，表單的名稱，屬性型別是表單的類型相同。  
  
> [!NOTE]
>  如果名稱有衝突時，要存取表單的屬性名稱是*RootNamespace*_*命名空間*\_*FormName*。 例如，假設名為兩種形式`Form1.`其中一種形式是否在根命名空間`WindowsApplication1`和命名空間`Namespace1`，存取透過該表單`My.Forms.WindowsApplication1_Namespace1_Form1`。  
  
 `My.Forms`物件提供在啟動時建立的應用程式的主要表單的執行個體的存取。 所有其他形式，`My.Forms`物件會建立表單的新執行個體，當它存取，並將它儲存。 後續嘗試存取該屬性會傳回該執行個體的格式。  
  
 您可以藉由指派處置表單`Nothing`設為該表單的屬性。 屬性 setter 呼叫<xref:System.Windows.Forms.Form.Close%2A>方法的表單，然後指派`Nothing`的預存值。 如果您指派任何值以外`Nothing`於屬性 setter 會擲回<xref:System.ArgumentException>例外狀況。  
  
 您可以測試的屬性是否`My.Forms`物件會儲存表單的執行個體使用`Is`或`IsNot`運算子。 您可以使用這些運算子，來檢查屬性的值是否為`Nothing`。  
  
> [!NOTE]
>  通常`Is`或`IsNot`操作員必須讀取要比較之屬性的值。 不過，如果屬性目前儲存`Nothing`，屬性會建立表單的新執行個體，並接著會傳回該執行個體。 不過，Visual Basic 編譯器會將屬性`My.Forms`物件以不同的方式，並可讓`Is`或`IsNot`運算子來檢查屬性的狀態，而不需要變更其值。  
  
## <a name="example"></a>範例  
 這個範例會變更的預設標題`SidebarMenu`表單。  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 此範例正常運作，您的專案必須表單名為`SidebarMenu`。  
  
 此程式碼將僅適用於的 Windows 應用程式專案。  
  
## <a name="requirements"></a>需求  
  
### <a name="availability-by-project-type"></a>專案類型的可用性  
  
|專案類型|可用|  
|---|---|  
|Windows 應用程式|**是**|  
|類別庫|否|  
|主控台應用程式|否|  
|Windows 控制項程式庫|否|  
|Web 控制項程式庫|否|  
|Windows 服務|否|  
|網站|否|  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [物件](../../../visual-basic/language-reference/objects/index.md)
- [Is 運算子](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 運算子](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [存取應用程式表單](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
