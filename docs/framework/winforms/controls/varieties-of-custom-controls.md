---
title: 各種自訂控制項
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], user controls
- controls [Windows Forms], types of
- composite controls [Windows Forms]
- extended controls [Windows Forms]
- controls [Windows Forms], extended
- user controls [Windows Forms]
- custom controls [Windows Forms]
- controls [Windows Forms], composite
ms.assetid: 3cea09e5-4344-4ccb-9858-b66ccac210ff
ms.openlocfilehash: cd78a0f2513d0e352efa1b1b866627586e6068bd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54683920"
---
# <a name="varieties-of-custom-controls"></a>各種自訂控制項
使用 .NET Framework，您可以開發及實作新的控制項。 您可以擴充熟悉的使用者控制項的功能，以及透過繼承擴充現有的控制項。 您也可以撰寫自訂控制項來執行它們自己的繪製。  
  
 決定要建立的控制項類型可能會令人困擾。 本主題著重於您可以繼承之各種控制項之間的差異，並且提供如何為專案選擇特定種類控制項的相關資訊。  
  
> [!NOTE]
>  如需撰寫控制項以在 Web Form 上使用的詳細資訊，請參閱[開發自訂 ASP.NET 伺服器控制項](https://msdn.microsoft.com/library/fbe26c16-cff4-4089-b3dd-877411f0c0ef)。  
  
## <a name="base-control-class"></a>基底控制項類別  
 <xref:System.Windows.Forms.Control>類別是基底類別，針對 Windows Form 控制項。 它提供視覺顯示 Windows Forms 應用程式所需的基礎結構。  
  
 <xref:System.Windows.Forms.Control>類別會執行下列工作來提供 Windows Forms 應用程式中的視覺顯示：  
  
-   公開視窗控制代碼。  
  
-   管理訊息路由。  
  
-   提供滑鼠和鍵盤事件，以及其他許多使用者介面事件。  
  
-   提供進階版面配置功能。  
  
-   包含特定的視覺顯示的許多屬性，例如<xref:System.Windows.Forms.Control.ForeColor%2A>， <xref:System.Windows.Forms.Control.BackColor%2A>， <xref:System.Windows.Forms.Control.Height%2A>，和<xref:System.Windows.Forms.Control.Width%2A>。  
  
-   提供 Windows Forms 控制項做為 Microsoft® ActiveX® 控制項所需的安全性和執行緒支援。  
  
 因為基底類別提供了非常多的基礎結構，所以開發您自己的 Windows Forms 控制項相對容易。  
  
## <a name="kinds-of-controls"></a>控制項種類  
 Windows Forms 支援三種使用者定義的控制項︰複合、擴充和自訂。 下列章節描述每一種控制項，並且提供選擇要用於專案類型的建議。  
  
### <a name="composite-controls"></a>複合控制項  
 複合控制項是封裝成通用容器的 Windows Forms 控制項的集合。 這類控制項有時候稱為「使用者控制項」。 包含的控制項稱為「組成控制項」。  
  
 複合控制項保存了與每個 Windows Forms 控制項相關聯的所有固有功能，並可讓您選擇性地公開和繫結其屬性。 複合控制項也提供大量的預設鍵盤處理功能，讓您在開發時不需要付出額外努力。  
  
 例如，可以建置複合控制項來顯示資料庫中的客戶地址資料。 此控制項包含<xref:System.Windows.Forms.DataGridView>控制項以顯示 [資料庫] 欄位中，<xref:System.Windows.Forms.BindingSource>來處理繫結至資料來源，和<xref:System.Windows.Forms.BindingNavigator>記錄之間移動的控制項。 您可以選擇性地公開資料繫結屬性，而整個控制項可以封裝，並且在各應用程式之間重複使用。 如需此類複合控制項的範例，請參閱[How to:在 Windows Form 控制項中套用屬性](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)。  
  
 若要撰寫複合控制項，衍生自<xref:System.Windows.Forms.UserControl>類別。 <xref:System.Windows.Forms.UserControl>基底類別提供鍵盤路由子控制項，並讓子系控制項做為群組運作。 如需詳細資訊，請參閱[開發複合 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)。  
  
 **建議**  
  
 如果有下列情況，便繼承自 <xref:System.Windows.Forms.UserControl> 類別：  
  
-   您想要將數個 Windows Form 控制項的功能結合成一個可重複使用的單位。  
  
### <a name="extended-controls"></a>擴充控制項  
 您可以從任何現有的 Windows Form 控制項衍生繼承的控制項。 使用這種方法，您可以保留 Windows Forms 控制項的所有固有功能，然後藉由新增自訂屬性、方法或其他功能，以擴充該功能。 使用這個選項，您可以覆寫基底控制項的繪製邏輯，然後藉由變更其外觀，以擴充其使用者介面。  
  
 例如，您可以建立衍生自控制項<xref:System.Windows.Forms.Button>控制追蹤多少次使用者按一下它。  
  
 在一些控制項中，您也可以將自訂外觀至您的控制項的圖形化使用者介面藉由覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>基底類別的方法。 延伸按鈕會追蹤點擊，您可以覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法呼叫的基底實作<xref:System.Windows.Forms.Control.OnPaint%2A>，然後的其中一個角落，繪製點擊計數和<xref:System.Windows.Forms.Button>控制項工作區。  
  
 **建議**  
  
 如果有下列情況，便繼承自 Windows Form 控制項：  
  
-   大部分的所需功能已經與現有的 Windows Form 控制項相同。  
  
-   您不需要自訂的圖形化使用者介面，或是您想要為現有的控制項設計新的圖形化使用者介面。  
  
### <a name="custom-controls"></a>自訂控制項  
 若要建立控制項的另一個方法是建立一個從頭藉由繼承自<xref:System.Windows.Forms.Control>。 <xref:System.Windows.Forms.Control>類別提供的所有控制項，包括滑鼠和鍵盤處理事件，所需的基本功能，但沒有控制項特定功能或圖形化介面。  
  
 建立控制項，藉由繼承自<xref:System.Windows.Forms.Control>類別需要更多的思考和投入時間，比繼承自<xref:System.Windows.Forms.UserControl>或現有的 Windows Form 控制項。 因為已為您保留許多實作，所以您的控制項比複合或擴充控制項具有更大的彈性，您可以量身打造您的控制項以符合您的確切需求。  
  
 若要實作自訂控制項，您必須撰寫程式碼<xref:System.Windows.Forms.Control.OnPaint%2A>控制項，以及任何您需要的功能特定程式碼的事件。 您也可以覆寫<xref:System.Windows.Forms.Control.WndProc%2A>方法及處理 windows 訊息直接。 這是建立控制項最強大的方式，但是若要有效使用這項技術，您必須先熟悉 Microsoft Win32® API。  
  
 自訂控制項的範例是複製類比時鐘外觀和行為的時鐘控制項。 若要讓時鐘指針移動以回應叫用自訂繪製<xref:System.Windows.Forms.Timer.Tick>自內部事件<xref:System.Windows.Forms.Timer>元件。 如需詳細資訊，請參閱[＜How to：開發簡單的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)。  
  
 **建議**  
  
 如果有下列情況，便繼承自 <xref:System.Windows.Forms.Control> 類別：  
  
-   您想要提供控制項的自訂圖形表示。  
  
-   您需要實作無法透過標準控制項使用的自訂功能。  
  
### <a name="activex-controls"></a>ActiveX 控制項  
 雖然 Windows Forms 基礎結構已進行最佳化來裝載 Windows Forms 控制項，但是您仍然可以使用 ActiveX 控制項。 在 Visual Studio 中會支援這項工作。 如需詳細資訊，請參閱[＜How to：將 ActiveX 控制項新增至 Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-activex-controls-to-windows-forms.md)。  
  
### <a name="windowless-controls"></a>無視窗控制項  
 Microsoft Visual Basic® 6.0 和 ActiveX 技術支援「無視窗」控制項。 在 Windows Forms 中不支援無視窗控制項。  
  
## <a name="custom-design-experience"></a>自訂設計體驗  
 如果您需要實作自訂設計階段經驗，您可以撰寫自己的設計工具。 對於複合控制項，衍生的自訂設計工具類別<xref:System.Windows.Forms.Design.ParentControlDesigner>或<xref:System.Windows.Forms.Design.DocumentDesigner>類別。 擴充和自訂控制項衍生您的自訂設計工具類別從<xref:System.Windows.Forms.Design.ControlDesigner>類別。  
  
 使用<xref:System.ComponentModel.DesignerAttribute>要與您的設計工具產生關聯您的控制項。 如需詳細資訊，請參閱 <<c0> [ 擴充設計階段支援](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)和[How to:建立採用設計階段功能的 Windows Form 控制項](https://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)。  
  
## <a name="see-also"></a>另請參閱
- [使用 .NET Framework 開發自訂的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [如何：開發簡單的 Windows Forms 控制項](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)
- [開發複合 Windows Forms 控制項](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)
- [擴充設計階段支援](https://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)
- [如何：建立採用設計階段功能的 Windows Form 控制項](https://msdn.microsoft.com/library/8e0bad0e-56f3-43d2-bf63-a945c654d97c)
