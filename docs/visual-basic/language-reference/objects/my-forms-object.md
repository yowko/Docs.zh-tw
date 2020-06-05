---
title: My.Forms 物件
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: 001f6fbfae2467ea0af5e98ca041b694d1e7b8f9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84372436"
---
# <a name="myforms-object"></a>My.Forms 物件

提供屬性，以存取目前專案中宣告之每個 Windows form 的實例。

## <a name="remarks"></a>備註

`My.Forms`物件會在目前的專案中提供每個表單的實例。 屬性的名稱與屬性所存取的表單名稱相同。

您可以使用表單的名稱來存取物件所提供的表單 `My.Forms` ，而不需要限定。 因為屬性名稱與表單的類型名稱相同，所以可讓您存取表單，就像它有預設的實例一樣。 例如，`My.Forms.Form1.Show` 等於 `Form1.Show`。

`My.Forms`物件只會公開與目前專案相關聯的表單。 它不會提供參考的 Dll 中所宣告之表單的存取權。 若要存取 DLL 提供的表單，您必須使用表單的限定名稱，此格式寫成*DllName*。*FormName*。

您可以使用 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> 屬性來取得應用程式所有開啟表單的集合。

物件及其屬性僅適用于 Windows 應用程式。

## <a name="properties"></a>屬性

物件的每個屬性都 `My.Forms` 可讓您存取目前專案中的表單實例。 屬性的名稱與屬性所存取的表單名稱相同，而且屬性類型與表單的類型相同。

> [!NOTE]
> 如果發生名稱衝突，存取表單的屬性名稱是*RootNamespace*_*Namespace* \_ *FormName*。 例如，假設有兩個表單名為， `Form1.` 如果其中一個表單是在根命名空間中， `WindowsApplication1` 而在命名空間中 `Namespace1` ，您會透過存取該表單 `My.Forms.WindowsApplication1_Namespace1_Form1` 。

`My.Forms`物件提供在啟動時所建立之應用程式主要表單實例的存取權。 對於所有其他表單， `My.Forms` 物件會在存取並儲存表單時，建立其新的實例。 後續嘗試存取該屬性時，會傳回該表單的實例。

您可以藉由指派 `Nothing` 給該表單的屬性來處置表單。 屬性 setter 會呼叫 <xref:System.Windows.Forms.Form.Close%2A> 表單的方法，然後將指派 `Nothing` 給儲存的值。 如果您將以外的任何值指派 `Nothing` 給屬性，setter 就會擲回 <xref:System.ArgumentException> 例外狀況。

您可以使用 or 運算子來測試物件的屬性是否 `My.Forms` 儲存表單的實例 `Is` `IsNot` 。 您可以使用這些運算子來檢查屬性的值是否為 `Nothing` 。

> [!NOTE]
> 一般而言， `Is` 或 `IsNot` 運算子必須讀取屬性的值，才能執行比較。 不過，如果屬性目前儲存 `Nothing` ，則屬性會建立表單的新實例，然後傳回該實例。 不過，Visual Basic 編譯器 `My.Forms` 會以不同的方式來處理物件的屬性，並允許 `Is` 或 `IsNot` 運算子檢查屬性的狀態，而不需要變更其值。

## <a name="example"></a>範例

這個範例會變更預設 `SidebarMenu` 表單的標題。

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

若要讓此範例能夠正常執行，您的專案必須具有名為的表單 `SidebarMenu` 。

這段程式碼只適用于 Windows 應用程式專案。

## <a name="requirements"></a>規格需求

### <a name="availability-by-project-type"></a>依專案類型的可用性

|專案類型|可用|
|---|---|
|Windows 應用程式|**是**|
|類別庫|No|
|主控台應用程式|No|
|Windows 控制項程式庫|No|
|Web 控制項程式庫|No|
|Windows 服務|No|
|網站|No|

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [物件](index.md)
- [Is 運算子](../operators/is-operator.md)
- [IsNot 運算子](../operators/isnot-operator.md)
- [存取應用程式表單](../../developing-apps/programming/accessing-application-forms.md)
