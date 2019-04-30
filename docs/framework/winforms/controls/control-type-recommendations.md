---
title: 控制項類型建議
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: 5dc734997917af7ec4a20a6c12ae04825507c7ce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011537"
---
# <a name="control-type-recommendations"></a>控制項類型建議
.NET Framework 可讓您有能力開發及實作新的控制項。 除了熟悉的使用者控制項，現在您會發現您也可以撰寫自訂控制項來執行它們自己的繪製，而且甚至能夠透過繼承，擴充現有控制項的功能。 決定要建立的控制項類型可能會令人困擾。 本章節強調您可以繼承的各類型控制項之間的差異，並提供關於為您的專案選擇類型的注意事項。  
  
> [!NOTE]
>  如果您想要撰寫 Web Forms 上使用的控制項，請參閱[開發自訂 ASP.NET 伺服器控制項](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100))。  
  
## <a name="inheriting-from-a-windows-forms-control"></a>繼承 Windows Form 控制項  
 您可以從任何現有的 Windows Form 控制項衍生繼承的控制項。 這種方法可讓您保留 Windows Form 控制項的所有固有功能，然後藉由加入自訂屬性、方法或其他功能，以擴充該功能。 例如，您可以建立從 <xref:System.Windows.Forms.TextBox> 衍生的控制項，它只接受數字，而且會自動將輸入轉換成值。 這類控制項可能會包含在文字方塊中的文字變更呼叫的驗證程式碼，而且可能會有一個額外的屬性 Value。 在一些控制項中，您也可以藉由覆寫基底類別的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法，將自訂外觀加入至控制項的圖形化介面。  
  
 如果有下列情況，便繼承自 Windows Form 控制項：  
  
- 大部分的所需功能已經與現有的 Windows Form 控制項相同。  
  
- 您不需要自訂的圖形化介面，或是您想要為現有的控制項設計新的圖形化前端。  
  
## <a name="inheriting-from-the-usercontrol-class"></a>繼承自 UserControl 類別  
 使用者控制項是封裝成通用容器的 Windows Form 控制項的集合。 容器保存了與每個 Windows Form 控制項相關聯的所有固有功能，並可讓您選擇性地公開 (expose) 和繫結其屬性。 使用者控制項的一個例子可能是建置用來顯示資料庫中客戶地址資料的控制項。 這個控制項可包括數個文字方塊來顯示每個欄位，以及按鈕控制項來巡覽記錄。 資料繫結屬性可以選擇性地公開，而整個控制項可以封裝，並且在各應用程式之間重複使用。  
  
 如果有下列情況，便繼承自 <xref:System.Windows.Forms.UserControl> 類別：  
  
- 您想要將數個 Windows Form 控制項的功能結合成一個可重複使用的單位。  
  
## <a name="inheriting-from-the-control-class"></a>繼承自 Control 類別  
 建立控制項的另一個方法是藉由繼承自 <xref:System.Windows.Forms.Control>，實際地從頭建立一個控制項。 <xref:System.Windows.Forms.Control> 類別會提供控制項所需的所有基本功能 (例如事件)，但不提供控制項特有的功能或圖形化介面。 藉由繼承自 <xref:System.Windows.Forms.Control> 類別來建立控制項，比繼承自使用者控制項或現有的 Windows Form 控制項需要更多的思考和投入工作。 作者必須撰寫控制項 <xref:System.Windows.Forms.Control.OnPaint%2A> 事件程式碼，以及任何所需的功能特定程式碼。 不過這允許更多的彈性，且您可以自訂控制項，以符合您的確切需求。 自訂控制項的一個例子是複製類比時鐘外觀和動作的時鐘控制項。 會叫用自訂繪製，讓時鐘指針移動以回應內部計時器元件的 <xref:System.Windows.Forms.Timer.Tick> 事件。  
  
 如果有下列情況，便繼承自 <xref:System.Windows.Forms.Control> 類別：  
  
- 您想要提供控制項的自訂圖形表示。  
  
- 您需要實作無法透過標準控制項使用的自訂功能。  
  
- [如何：顯示中的控制項選擇工具箱項目對話方塊](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
  
- [逐步解說：序列化標準類型使用 DesignerSerializationVisibilityAttribute 集合](serializing-collections-designerserializationvisibilityattribute.md)  
  
- [逐步解說：繼承自具有視覺效果的 Windows Forms 控制項C#](walkthrough-inheriting-from-a-windows-forms-control-with-visual-csharp.md)  
  
- [如何：為控制項提供工具箱點陣圖](how-to-provide-a-toolbox-bitmap-for-a-control.md)  
  
- [如何：繼承自現有的 Windows Forms 控制項](how-to-inherit-from-existing-windows-forms-controls.md)  
  
- [逐步解說：在設計階段針對自訂 Windows Forms 控制項進行偵錯](walkthrough-debugging-custom-windows-forms-controls-at-design-time.md)  
  
- [如何：繼承自 Control 類別](how-to-inherit-from-the-control-class.md)  
  
- [如何：測試 UserControl 的執行階段行為](how-to-test-the-run-time-behavior-of-a-usercontrol.md)  
  
- [如何：將控制項和表單邊緣對齊在設計階段](how-to-align-a-control-to-the-edges-of-forms-at-design-time.md)  
  
- [如何：繼承自 UserControl 類別](how-to-inherit-from-the-usercontrol-class.md)  
  
- [如何：撰寫 Windows forms 的控制項](how-to-author-controls-for-windows-forms.md)  
  
- [如何：撰寫複合控制項](how-to-author-composite-controls.md)  
  
- [逐步解說：撰寫使用 Visual Basic 複合控制項](walkthrough-authoring-a-composite-control-with-visual-basic.md)  
  
- [逐步解說：撰寫複合控制項具有視覺效果C#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
  
- [逐步解說：繼承自使用 Visual Basic 的 Windows Forms 控制項](walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic.md)  
  
- [逐步解說：建立利用 Visual Studio 設計階段功能的 Windows Form 控制項](creating-a-wf-control-design-time-features.md)  
  
- [如何：建立採用設計階段功能的 Windows Form 控制項](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))  
  
## <a name="see-also"></a>另請參閱

- [如何：開發簡單的 Windows Forms 控制項](how-to-develop-a-simple-windows-forms-control.md)
- [各種自訂控制項](varieties-of-custom-controls.md)
