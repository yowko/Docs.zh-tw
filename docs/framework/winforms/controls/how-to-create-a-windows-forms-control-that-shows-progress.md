---
title: HOW TO：建立顯示進度的 Windows Forms 控制項
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
ms.openlocfilehash: 1f457d6e2b0eb73da7a16dc93ea80a14ddb4b2c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202010"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>HOW TO：建立顯示進度的 Windows Forms 控制項
下列程式碼範例會顯示稱為 `FlashTrackBar` 的自訂控制項，其可用來對使用者顯示應用程式的層級或進度。 它會使用漸層來以視覺方式表示進度。  
  
 `FlashTrackBar` 控制項可說明下列概念︰  
  
-   定義自訂屬性。  
  
-   定義自訂事件。 (`FlashTrackBar` 會定義 `ValueChanged` 事件。)  
  
-   覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法，以提供繪製控制項的邏輯。  
  
-   計算區域可用於繪製控制項使用其<xref:System.Windows.Forms.Control.ClientRectangle%2A>屬性。 `FlashTrackBar` 這會以其`OptimizedInvalidate`方法。  
  
-   在 Windows Forms 設計工具中變更屬性時，請實作該屬性的序列化或持續性。 `FlashTrackBar` 定義`ShouldSerializeStartColor`並`ShouldSerializeEndColor`方法來序列化其`StartColor`和`EndColor`屬性。  
  
 下表顯示 `FlashTrackBar` 所定義的自訂屬性。  
  
|屬性|描述|  
|--------------|-----------------|  
|`AllowUserEdit`|指出使用者是否可藉由按一下並拖曳快速追蹤列來變更其值。|  
|`EndColor`|指定追蹤列的結束色彩。|  
|`DarkenBy`|指定要將有關前景漸層的背景加深的程度。|  
|`Max`|指定追蹤列的最大值。|  
|`Min`|指定追蹤列的最小值。|  
|`StartColor`|指定漸層的開始色彩。|  
|`ShowPercentage`|指出是否要顯示漸層的百分比。|  
|`ShowValue`|指出是否要顯示漸層的目前值。|  
|`ShowGradient`|表示追蹤列是否應顯示色彩漸層，以顯示目前的值。|  
|-   `Value`|指定追蹤列的目前值。|  
  
 下表顯示 `FlashTrackBar:` 所定義的其他成員：引發事件的屬性變更事件和方法。  
  
|成員|描述|  
|------------|-----------------|  
|`ValueChanged`|當追蹤列的 `Value` 屬性變更時所引發的事件。|  
|`OnValueChanged`|引發 `ValueChanged` 事件的方法。|  
  
> [!NOTE]
>  `FlashTrackBar` 會使用<xref:System.EventArgs>事件資料的類別和<xref:System.EventHandler>事件委派。  
  
 為了處理對應*EventName*事件`FlashTrackBar`覆寫下列方法，它繼承自<xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
-   <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
-   <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 為了處理對應的屬性變更事件，`FlashTrackBar`覆寫下列方法，它繼承自<xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
-   <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>範例  
 `FlashTrackBar` 控制項會定義兩個 UI 類型編輯器：`FlashTrackBarValueEditor` 和 `FlashTrackBarDarkenByEditor`，兩者均顯示於下列程式碼清單中。 `HostApp` 類別會在 Windows Form 上使用 `FlashTrackBar` 控制項。  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a>另請參閱

- [擴充設計階段支援](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Windows Form 控制項開發的基本概念](windows-forms-control-development-basics.md)
