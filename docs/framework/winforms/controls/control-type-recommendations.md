---
title: 控制項類型建議
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- user controls [Windows Forms], when to use
- custom controls [Windows Forms], types
- controls [Windows Forms], creating
ms.assetid: 5235fe9d-c36a-4c08-ae76-6cb90b50085e
ms.openlocfilehash: d6a2b663c566aae48c694ffc335fcef0ce24034f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="control-type-recommendations"></a>控制項類型建議
.NET Framework 可讓您有能力開發及實作新的控制項。 除了熟悉的使用者控制項，現在您會發現您也可以撰寫自訂控制項來執行它們自己的繪製，而且甚至能夠透過繼承，擴充現有控制項的功能。 決定要建立的控制項類型可能會令人困擾。 本章節強調您可以繼承的各類型控制項之間的差異，並提供關於為您的專案選擇類型的注意事項。  
  
> [!NOTE]
>  如果您想要撰寫 Web Forms 上使用的控制項，請參閱[開發自訂 ASP.NET 伺服器控制項](http://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef)。  
  
## <a name="inheriting-from-a-windows-forms-control"></a>繼承 Windows Form 控制項  
 您可以從任何現有的 Windows Form 控制項衍生繼承的控制項。 這種方法可讓您保留 Windows Form 控制項的所有固有功能，然後藉由加入自訂屬性、方法或其他功能，以擴充該功能。 例如，您可以建立從 <xref:System.Windows.Forms.TextBox> 衍生的控制項，它只接受數字，而且會自動將輸入轉換成值。 這類控制項可能會包含在文字方塊中的文字變更呼叫的驗證程式碼，而且可能會有一個額外的屬性 Value。 在一些控制項中，您也可以藉由覆寫基底類別的 <xref:System.Windows.Forms.Control.OnPaint%2A> 方法，將自訂外觀加入至控制項的圖形化介面。  
  
 如果有下列情況，便繼承自 Windows Form 控制項：  
  
-   大部分的所需功能已經與現有的 Windows Form 控制項相同。  
  
-   您不需要自訂的圖形化介面，或是您想要為現有的控制項設計新的圖形化前端。  
  
## <a name="inheriting-from-the-usercontrol-class"></a>繼承自 UserControl 類別  
 使用者控制項是封裝成通用容器的 Windows Form 控制項的集合。 容器保存了與每個 Windows Form 控制項相關聯的所有固有功能，並可讓您選擇性地公開 (expose) 和繫結其屬性。 使用者控制項的一個例子可能是建置用來顯示資料庫中客戶地址資料的控制項。 這個控制項可包括數個文字方塊來顯示每個欄位，以及按鈕控制項來巡覽記錄。 資料繫結屬性可以選擇性地公開，而整個控制項可以封裝，並且在各應用程式之間重複使用。  
  
 如果有下列情況，便繼承自 <xref:System.Windows.Forms.UserControl> 類別：  
  
-   您想要將數個 Windows Form 控制項的功能結合成一個可重複使用的單位。  
  
## <a name="inheriting-from-the-control-class"></a>繼承自 Control 類別  
 建立控制項的另一個方法是藉由繼承自 <xref:System.Windows.Forms.Control>，實際地從頭建立一個控制項。 <xref:System.Windows.Forms.Control> 類別會提供控制項所需的所有基本功能 (例如事件)，但不提供控制項特有的功能或圖形化介面。 藉由繼承自 <xref:System.Windows.Forms.Control> 類別來建立控制項，比繼承自使用者控制項或現有的 Windows Form 控制項需要更多的思考和投入工作。 作者必須撰寫控制項 <xref:System.Windows.Forms.Control.OnPaint%2A> 事件程式碼，以及任何所需的功能特定程式碼。 不過這允許更多的彈性，且您可以自訂控制項，以符合您的確切需求。 自訂控制項的一個例子是複製類比時鐘外觀和動作的時鐘控制項。 會叫用自訂繪製，讓時鐘指針移動以回應內部計時器元件的 <xref:System.Windows.Forms.Timer.Tick> 事件。  
  
 如果有下列情況，便繼承自 <xref:System.Windows.Forms.Control> 類別：  
  
-   您想要提供控制項的自訂圖形表示。  
  
-   您需要實作無法透過標準控制項使用的自訂功能。  
  
-   [操作說明：在選擇工具箱項目對話方塊中顯示控制項](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))  
  
-   [逐步解說：使用 DesignerSerializationVisibilityAttribute 序列化標準類型的集合](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))  
  
-   [逐步解說：使用 Visual C# 繼承自 Windows Forms 控制項](http://msdn.microsoft.com/library/5h0k2e6x\(v=vs.110\))  
  
-   [操作說明：為控制項提供工具箱點陣圖](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))  
  
-   [操作說明：繼承自現有的 Windows Forms 控制項](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))  
  
-   [逐步解說：在設計階段偵錯自訂的 Windows Forms 控制項](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))  
  
-   [如何：繼承自 Control 類別](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))  
  
-   [操作說明：測試 UserControl 的執行階段行為](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))  
  
-   [操作說明：在設計階段將控制項對齊表單邊緣](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))  
  
-   [操作說明：繼承自 UserControl 類別](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))  
  
-   [如何：撰寫 Windows Forms 的控制項](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))  
  
-   [如何：撰寫複合控制項](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))  
  
-   [逐步解說：使用 Visual Basic 撰寫複合控制項](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))  
  
-   [逐步解說：使用 Visual C# 撰寫複合控制項](http://msdn.microsoft.com/library/a6h7e207\(v=vs.110\))  
  
-   [逐步解說：使用 Visual Basic 繼承自 Windows Forms 控制項](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))  
  
-   [如何：建立採用設計階段功能的 Windows Forms 控制項](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))  
  
-   [如何：建立採用設計階段功能的 Windows Forms 控制項](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))  
  
## <a name="see-also"></a>另請參閱  
 [操作說明：開發簡單的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [各種自訂控制項](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
