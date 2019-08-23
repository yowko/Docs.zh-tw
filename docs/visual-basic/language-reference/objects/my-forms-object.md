---
title: Forms 物件 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 9fa5c77dd12c98100e3d17fc473a6802180d1e32
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965974"
---
# <a name="myforms-object"></a>My.Forms 物件
提供屬性, 以存取目前專案中宣告之每個 Windows form 的實例。  
  
## <a name="remarks"></a>備註  
 `My.Forms`物件會在目前的專案中提供每個表單的實例。 屬性的名稱與屬性所存取的表單名稱相同。   
  
 您可以使用表單的名稱來`My.Forms`存取物件所提供的表單, 而不需要限定。 因為屬性名稱與表單的類型名稱相同, 所以可讓您存取表單, 就像它有預設的實例一樣。 例如，`My.Forms.Form1.Show` 等於 `Form1.Show`。  
  
 `My.Forms`物件只會公開與目前專案相關聯的表單。 它不會提供參考的 Dll 中所宣告之表單的存取權。 若要存取 DLL 提供的表單, 您必須使用表單的限定名稱, 此格式寫成*DllName*。*FormName*。  
  
 您可以使用<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>屬性來取得應用程式所有開啟表單的集合。  
  
 物件及其屬性僅適用于 Windows 應用程式。  
  
## <a name="properties"></a>屬性  
 `My.Forms`物件的每個屬性都可讓您存取目前專案中的表單實例。 屬性的名稱與屬性所存取的表單名稱相同, 而且屬性類型與表單的類型相同。  
  
> [!NOTE]
> 如果發生名稱衝突, 存取表單的屬性名稱是*RootNamespace*_*Namespace* \_ *FormName*。 例如, 假設有兩個窗`Form1.`體名為, 如果其中一個表單是`WindowsApplication1`在根命名空間`Namespace1`中, 而在命名空間中`My.Forms.WindowsApplication1_Namespace1_Form1`, 您會透過存取該表單。  
  
 `My.Forms`物件提供在啟動時所建立之應用程式主要表單實例的存取權。 對於所有其他表單, `My.Forms`物件會在存取並儲存表單時, 建立其新的實例。 後續嘗試存取該屬性時, 會傳回該表單的實例。  
  
 您可以藉由指派`Nothing`給該表單的屬性來處置表單。 屬性 setter 會呼叫<xref:System.Windows.Forms.Form.Close%2A>表單的方法, 然後將指派`Nothing`給儲存的值。 如果您將以外`Nothing`的任何值指派給屬性, setter <xref:System.ArgumentException>就會擲回例外狀況。  
  
 您可以`My.Forms` `Is`使用or`IsNot`運算子來測試物件的屬性是否儲存表單的實例。 您可以使用這些運算子來檢查屬性的值是否為`Nothing`。  
  
> [!NOTE]
> 一般而言, `Is`或`IsNot`運算子必須讀取屬性的值, 才能執行比較。 不過, 如果屬性目前儲存`Nothing`, 則屬性會建立表單的新實例, 然後傳回該實例。 不過, Visual Basic 編譯器會以不同的方式來`My.Forms`處理物件的屬性, `Is`並`IsNot`允許或運算子檢查屬性的狀態, 而不需要變更其值。  
  
## <a name="example"></a>範例  
 這個範例會變更預設`SidebarMenu`表單的標題。  
  
 [!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]  
  
 若要讓此範例能夠正常執行, 您的專案必須`SidebarMenu`具有名為的表單。  
  
 這段程式碼只適用于 Windows 應用程式專案。  
  
## <a name="requirements"></a>需求  
  
### <a name="availability-by-project-type"></a>依專案類型的可用性  
  
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
