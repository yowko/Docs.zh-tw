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
ms.openlocfilehash: 106da550fc6e6c50bc40e103e1f855059a9ffa9c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950097"
---
# <a name="varieties-of-custom-controls"></a>各種自訂控制項
使用 .NET Framework，您可以開發及實作新的控制項。 您可以擴充熟悉的使用者控制項的功能，以及透過繼承擴充現有的控制項。 您也可以撰寫自訂控制項來執行它們自己的繪製。  
  
 決定要建立的控制項類型可能會令人困擾。 本主題著重於您可以繼承之各種控制項之間的差異，並且提供如何為專案選擇特定種類控制項的相關資訊。  
  
> [!NOTE]
> 如需撰寫控制項以在 Web Form 上使用的詳細資訊，請參閱[開發自訂 ASP.NET 伺服器控制項](https://docs.microsoft.com/previous-versions/aspnet/zt27tfhy(v=vs.100))。  
  
## <a name="base-control-class"></a>基底控制項類別  
 <xref:System.Windows.Forms.Control>類別是 Windows Forms 控制項的基類。 它提供視覺顯示 Windows Forms 應用程式所需的基礎結構。  
  
 <xref:System.Windows.Forms.Control>類別會執行下列工作, 以在 Windows Forms 應用程式中提供視覺效果顯示:  
  
- 公開視窗控制代碼。  
  
- 管理訊息路由。  
  
- 提供滑鼠和鍵盤事件，以及其他許多使用者介面事件。  
  
- 提供進階版面配置功能。  
  
- 包含許多視覺效果顯示特有的屬性, 例如<xref:System.Windows.Forms.Control.ForeColor%2A>、 <xref:System.Windows.Forms.Control.BackColor%2A>、 <xref:System.Windows.Forms.Control.Height%2A>和<xref:System.Windows.Forms.Control.Width%2A>。  
  
- 提供 Windows Forms 控制項做為 Microsoft® ActiveX® 控制項所需的安全性和執行緒支援。  
  
 因為基底類別提供了非常多的基礎結構，所以開發您自己的 Windows Forms 控制項相對容易。  
  
## <a name="kinds-of-controls"></a>控制項種類  
 Windows Forms 支援三種使用者定義的控制項︰複合、擴充和自訂。 下列章節描述每一種控制項，並且提供選擇要用於專案類型的建議。  
  
### <a name="composite-controls"></a>複合控制項  
 複合控制項是封裝成通用容器的 Windows Forms 控制項的集合。 這類控制項有時候稱為「使用者控制項」。 包含的控制項稱為「組成控制項」。  
  
 複合控制項保存了與每個 Windows Forms 控制項相關聯的所有固有功能，並可讓您選擇性地公開和繫結其屬性。 複合控制項也提供大量的預設鍵盤處理功能，讓您在開發時不需要付出額外努力。  
  
 例如，可以建置複合控制項來顯示資料庫中的客戶地址資料。 這個控制項可以包含<xref:System.Windows.Forms.DataGridView>控制項來顯示資料庫欄位、用<xref:System.Windows.Forms.BindingSource>來處理<xref:System.Windows.Forms.BindingNavigator>資料來源的系結, 以及可在記錄中移動的控制項。 您可以選擇性地公開資料繫結屬性，而整個控制項可以封裝，並且在各應用程式之間重複使用。 如需這種複合控制項的範例, 請參閱[如何:在 Windows Forms 控制項](how-to-apply-attributes-in-windows-forms-controls.md)中套用屬性。  
  
 若要撰寫複合控制項, 請從<xref:System.Windows.Forms.UserControl>類別衍生。 <xref:System.Windows.Forms.UserControl>基類提供子控制項的鍵盤路由, 可讓子控制項當做群組來使用。 如需詳細資訊，請參閱[開發複合 Windows Forms 控制項](developing-a-composite-windows-forms-control.md)。  
  
 **建議**  
  
 如果有下列情況，便繼承自 <xref:System.Windows.Forms.UserControl> 類別：  
  
- 您想要將數個 Windows Form 控制項的功能結合成一個可重複使用的單位。  
  
### <a name="extended-controls"></a>擴充控制項  
 您可以從任何現有的 Windows Form 控制項衍生繼承的控制項。 使用這種方法，您可以保留 Windows Forms 控制項的所有固有功能，然後藉由新增自訂屬性、方法或其他功能，以擴充該功能。 使用這個選項，您可以覆寫基底控制項的繪製邏輯，然後藉由變更其外觀，以擴充其使用者介面。  
  
 例如, 您可以建立一個衍生自<xref:System.Windows.Forms.Button>控制項的控制項, 以追蹤使用者已按過的次數。  
  
 在某些控制項中, 您也可以藉由覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>基類的方法, 將自訂外觀加入控制項的圖形化使用者介面中。 針對追蹤按一下的擴充按鈕, 您可以覆寫<xref:System.Windows.Forms.Control.OnPaint%2A>方法以呼叫的基底<xref:System.Windows.Forms.Control.OnPaint%2A>實作為, 然後<xref:System.Windows.Forms.Button>在控制項工作區的一個角落繪製按一下計數。  
  
 **建議**  
  
 如果有下列情況，便繼承自 Windows Form 控制項：  
  
- 大部分的所需功能已經與現有的 Windows Form 控制項相同。  
  
- 您不需要自訂的圖形化使用者介面，或是您想要為現有的控制項設計新的圖形化使用者介面。  
  
### <a name="custom-controls"></a>自訂控制項  
 建立控制項的另一種方式是從繼承<xref:System.Windows.Forms.Control>, 一開始就從頭建立。 <xref:System.Windows.Forms.Control>類別提供控制項所需的所有基本功能, 包括滑鼠和鍵盤處理事件, 但不含控制項特定功能或圖形化介面。  
  
 從<xref:System.Windows.Forms.Control>類別繼承來建立控制項, 需要比繼承自<xref:System.Windows.Forms.UserControl>或現有 Windows Forms 控制項更多的想法和工作。 因為已為您保留許多實作，所以您的控制項比複合或擴充控制項具有更大的彈性，您可以量身打造您的控制項以符合您的確切需求。  
  
 若要執行自訂控制項, 您必須撰寫控制項<xref:System.Windows.Forms.Control.OnPaint%2A>事件的程式碼, 以及所需的任何功能特定程式碼。 您也可以覆寫<xref:System.Windows.Forms.Control.WndProc%2A>方法並直接處理 windows 訊息。 這是建立控制項最強大的方式，但是若要有效使用這項技術，您必須先熟悉 Microsoft Win32® API。  
  
 自訂控制項的範例是複製類比時鐘外觀和行為的時鐘控制項。 系統會叫用自訂繪製, 以回應<xref:System.Windows.Forms.Timer.Tick>內部<xref:System.Windows.Forms.Timer>元件中的事件。 如需詳細資訊，請參閱[如何：開發簡單的 Windows Forms 控制項](how-to-develop-a-simple-windows-forms-control.md)。  
  
 **建議**  
  
 如果有下列情況，便繼承自 <xref:System.Windows.Forms.Control> 類別：  
  
- 您想要提供控制項的自訂圖形表示。  
  
- 您需要實作無法透過標準控制項使用的自訂功能。  
  
### <a name="activex-controls"></a>ActiveX 控制項  
 雖然 Windows Forms 基礎結構已進行最佳化來裝載 Windows Forms 控制項，但是您仍然可以使用 ActiveX 控制項。 在 Visual Studio 中會支援這項工作。 如需詳細資訊，請參閱[如何：將 ActiveX 控制項新增至](how-to-add-activex-controls-to-windows-forms.md)Windows Forms。  
  
### <a name="windowless-controls"></a>無視窗控制項  
 Microsoft Visual Basic® 6.0 和 ActiveX 技術支援「無視窗」控制項。 在 Windows Forms 中不支援無視窗控制項。  
  
## <a name="custom-design-experience"></a>自訂設計體驗  
 如果您需要實作自訂設計階段經驗，您可以撰寫自己的設計工具。 針對複合控制項, 從<xref:System.Windows.Forms.Design.ParentControlDesigner> <xref:System.Windows.Forms.Design.DocumentDesigner>或類別衍生您的自訂設計工具類別。 針對擴充和自訂控制項, 從<xref:System.Windows.Forms.Design.ControlDesigner>類別衍生您的自訂設計工具類別。  
  
 <xref:System.ComponentModel.DesignerAttribute>使用將您的控制項與設計工具產生關聯。 如需詳細資訊, 請參閱[擴充設計階段支援](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))和[如何:建立會利用設計階段功能](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))的 Windows Forms 控制項。  
  
## <a name="see-also"></a>另請參閱

- [使用 .NET Framework 開發自訂的 Windows Forms 控制項](developing-custom-windows-forms-controls.md)
- [如何：開發簡單的 Windows Forms 控制項](how-to-develop-a-simple-windows-forms-control.md)
- [開發複合 Windows Forms 控制項](developing-a-composite-windows-forms-control.md)
- [擴充設計階段支援](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [如何：建立會利用設計階段功能的 Windows Forms 控制項](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/307hck25(v=vs.120))
