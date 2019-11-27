---
title: My.Forms 物件
ms.date: 07/20/2015
f1_keywords:
- My.Forms
- My.MyProject.Forms
helpviewer_keywords:
- My.Forms object
ms.assetid: f6bff4e6-6769-4294-956b-037aa6106d2a
ms.openlocfilehash: db86704fdc8120ccac5f4489c80a515834ad888f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350365"
---
# <a name="myforms-object"></a>My.Forms 物件

提供屬性，以存取目前專案中宣告之每個 Windows form 的實例。

## <a name="remarks"></a>備註

`My.Forms` 物件會在目前的專案中提供每個表單的實例。 屬性的名稱與屬性所存取的表單名稱相同。

您可以使用表單的名稱，而不需限定，來存取 `My.Forms` 物件所提供的表單。 因為屬性名稱與表單的類型名稱相同，所以可讓您存取表單，就像它有預設的實例一樣。 例如，`My.Forms.Form1.Show` 等於 `Form1.Show`。

`My.Forms` 物件只會公開與目前專案相關聯的表單。 它不會提供參考的 Dll 中所宣告之表單的存取權。 若要存取 DLL 提供的表單，您必須使用表單的限定名稱，此格式寫成*DllName*。*FormName*。

您可以使用 <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A> 屬性來取得應用程式所有開啟表單的集合。

物件及其屬性僅適用于 Windows 應用程式。

## <a name="properties"></a>內容

`My.Forms` 物件的每個屬性都可讓您存取目前專案中的表單實例。 屬性的名稱與屬性所存取的表單名稱相同，而且屬性類型與表單的類型相同。

> [!NOTE]
> 如果發生名稱衝突，存取表單的屬性名稱是*RootNamespace*_*Namespace*\_*FormName*。 例如，假設有兩個名為 `Form1.`的表單，如果其中一個表單是在根命名空間中 `WindowsApplication1` 而且在命名空間 `Namespace1`中，您會透過 `My.Forms.WindowsApplication1_Namespace1_Form1`來存取該表單。

`My.Forms` 物件提供在啟動時所建立之應用程式主要表單實例的存取權。 對於所有其他表單，`My.Forms` 物件會在存取並儲存表單時，建立其新的實例。 後續嘗試存取該屬性時，會傳回該表單的實例。

您可以藉由將 `Nothing` 指派給該表單的屬性來處置表單。 屬性 setter 會呼叫表單的 <xref:System.Windows.Forms.Form.Close%2A> 方法，然後將 `Nothing` 指派給儲存的值。 如果您將 `Nothing` 以外的任何值指派給屬性，則 setter 會擲回 <xref:System.ArgumentException> 例外狀況。

您可以使用 `Is` 或 `IsNot` 運算子，測試 `My.Forms` 物件的屬性是否儲存表單的實例。 您可以使用這些運算子來檢查屬性的值是否為 `Nothing`。

> [!NOTE]
> 一般來說，`Is` 或 `IsNot` 運算子必須讀取屬性的值，才能執行比較。 不過，如果屬性目前儲存 `Nothing`，則屬性會建立表單的新實例，然後傳回該實例。 不過，Visual Basic 編譯器會以不同的方式來處理 `My.Forms` 物件的屬性，並允許 `Is` 或 `IsNot` 運算子檢查屬性的狀態，而不需要變更其值。

## <a name="example"></a>範例

這個範例會變更預設 `SidebarMenu` 表單的標題。

[!code-vb[VbVbalrMyForms#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyForms/VB/Class1.vb#2)]

若要讓此範例能夠正常執行，您的專案必須具有名為 `SidebarMenu`的表單。

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

## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.ApplicationServices.WindowsFormsApplicationBase.OpenForms%2A>
- <xref:System.Windows.Forms.Form>
- <xref:System.Windows.Forms.Form.Close%2A>
- [物件](../../../visual-basic/language-reference/objects/index.md)
- [Is 運算子](../../../visual-basic/language-reference/operators/is-operator.md)
- [IsNot 運算子](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [存取應用程式表單](../../../visual-basic/developing-apps/programming/accessing-application-forms.md)
