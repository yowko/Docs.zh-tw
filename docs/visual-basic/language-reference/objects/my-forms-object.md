---
title: My.Forms 物件
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 4d6bb371b13dfb3fb735223b2a6a6a35e1416593
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603895"
---
# <a name="myforms-object"></a>My.Forms 物件
提供存取目前的專案中所宣告的每個 Windows form 的執行個體的屬性。  
  
## <a name="remarks"></a>備註  
 `My.Forms`物件提供每個表單目前專案中的執行個體。 屬性的名稱是表單的屬性存取的名稱相同。   
  
 您可以存取所提供的表單`My.Forms`使用的表單，而不加限定的名稱。 因為屬性名稱做為表單的類型名稱相同，這可讓您存取表單，如同它已有預設的執行個體。 例如，`My.Forms.Form1.Show` 等於 `Form1.Show`。  
  
 `My.Forms`物件會公開只與目前的專案相關聯的表單。 它不提供宣告中被參考 Dll 的表單的存取權。 若要存取的 DLL 所提供的表單，您必須使用限定的名稱的格式，撰寫為*DllName*。*FormName*。  
  
 您可以使用<xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>屬性來取得集合中的應用程式的所有開啟表單。  
  
 物件和其屬性的僅適用於 Windows 應用程式。  
  
## <a name="properties"></a>屬性  
 每一個屬性的`My.Forms`物件提供存取目前的專案中的表單之執行個體。 屬性的名稱與相同的屬性存取，表單的名稱，屬性類型就是表單的類型相同。  
  
> [!NOTE]
>  如果沒有名稱衝突，存取表單的屬性名稱是*RootNamespace*_*命名空間*\_*FormName*。 例如，假設名為兩種形式`Form1.`其中一個表單是否在根命名空間`WindowsApplication1`和命名空間`Namespace1`，存取透過該表單`My.Forms.WindowsApplication1_Namespace1_Form1`。  
  
 `My.Forms`物件提供存取的應用程式的主要表單，以在啟動時建立執行個體。 對於所有其他的表單，`My.Forms`時它存取，並將其物件會建立表單的新執行個體。 後續嘗試存取該屬性會傳回該執行個體的表單。  
  
 您可以藉由指派處置表單`Nothing`設為該表單的屬性。 屬性 setter 呼叫<xref:System.Windows.Forms.Form.Close%2A>方法的表單，然後指派`Nothing`儲存值。 如果您指派以外的任何值`Nothing`於屬性 setter 會擲回<xref:System.ArgumentException>例外狀況。  
  
 您可以測試是否屬性`My.Forms`物件儲存表單的執行個體使用`Is`或`IsNot`運算子。 您可以使用這些運算子來檢查屬性的值是否為`Nothing`。  
  
> [!NOTE]
>  一般而言，`Is`或`IsNot`運算子具有讀取要比較之屬性的值。 不過，如果屬性目前儲存`Nothing`，屬性建立表單的新執行個體，然後傳回該執行個體。 不過，Visual Basic 編譯器會將屬性`My.Forms`物件以不同的方式，並可讓`Is`或`IsNot`運算子來檢查屬性狀態，而不會變更其值。  
  
## <a name="example"></a>範例  
 這個範例會變更預設的標題`SidebarMenu`表單。  
  
 [!code-vb[VbVbalrMyForms#2](../../../visual-basic/language-reference/objects/codesnippet/VisualBasic/my-forms-object_1.vb)]  
  
 要讓範例能夠運作，您的專案必須擁有名為表單`SidebarMenu`。  
  
 這段程式碼只會在 Windows 應用程式專案。  
  
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
 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>  
 <xref:System.Windows.Forms.Form>  
 <xref:System.Windows.Forms.Form.Close%2A>  
 [物件](../../../visual-basic/language-reference/objects/index.md)  
 [Is 運算子](../../../visual-basic/language-reference/operators/is-operator.md)  
 [IsNot 運算子](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [存取應用程式表單](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
