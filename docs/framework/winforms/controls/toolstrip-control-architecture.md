---
title: "ToolStrip 控制項架構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6884598e6b883ab5e6369be5f2f796a194c7f930
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="toolstrip-control-architecture"></a>ToolStrip 控制項架構
<xref:System.Windows.Forms.ToolStrip>和<xref:System.Windows.Forms.ToolStripItem>類別可提供彈性、 可延伸系統顯示工具列、 狀態和功能表項目。 這些類別包含在<xref:System.Windows.Forms>命名空間和其所有通常以"ToolStrip"前置詞命名 (例如<xref:System.Windows.Forms.ToolStripOverflow>) 或 「 帶狀 」 的後置詞 (例如<xref:System.Windows.Forms.MenuStrip>)。  
  
## <a name="toolstrip"></a>ToolStrip  
 下列主題將描述<xref:System.Windows.Forms.ToolStrip>和從它衍生的控制項。  
  
 <xref:System.Windows.Forms.ToolStrip>是抽象的基底類別，如<xref:System.Windows.Forms.MenuStrip>， <xref:System.Windows.Forms.StatusStrip>，和<xref:System.Windows.Forms.ContextMenuStrip>。 下列物件模型顯示<xref:System.Windows.Forms.ToolStrip>繼承階層架構。  
  
 ![ToolStrip 物件模型](../../../../docs/framework/winforms/controls/media/toolstripobjectmodel.gif "ToolStripObjectModel")  
ToolStrip 物件模型  
  
 您可以存取中的所有項目<xref:System.Windows.Forms.ToolStrip>透過<xref:System.Windows.Forms.ToolStrip.Items%2A>集合。 您可以存取中的所有項目<xref:System.Windows.Forms.ToolStripDropDownItem>透過<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A>集合。 從衍生類別中<xref:System.Windows.Forms.ToolStrip>，您也可以使用<xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A>屬性來存取目前顯示的項目。 這些是目前不在溢位功能表中的項目。  
  
 下列項目專為緊密地與這兩個<xref:System.Windows.Forms.ToolStripSystemRenderer>和<xref:System.Windows.Forms.ToolStripProfessionalRenderer>中所有方向。 它們是在設計階段的預設可用的<xref:System.Windows.Forms.ToolStrip>控制項：  
  
-   <xref:System.Windows.Forms.ToolStripButton>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="menustrip"></a>MenuStrip  
 <xref:System.Windows.Forms.MenuStrip>已取代的最上層容器<xref:System.Windows.Forms.MainMenu>。 它也提供索引鍵的處理和多個文件介面 (MDI) 功能。 在功能上，<xref:System.Windows.Forms.ToolStripDropDownItem>和<xref:System.Windows.Forms.ToolStripMenuItem>連同工作<xref:System.Windows.Forms.MenuStrip>，不過它們衍生自<xref:System.Windows.Forms.ToolStripItem>。  
  
 下列項目專為緊密地與這兩個<xref:System.Windows.Forms.ToolStripSystemRenderer>和<xref:System.Windows.Forms.ToolStripProfessionalRenderer>中所有方向。 它們是在設計階段的預設可用的<xref:System.Windows.Forms.MenuStrip>控制項：  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="statusstrip"></a>StatusStrip  
 <xref:System.Windows.Forms.StatusStrip>取代<xref:System.Windows.Forms.StatusBar>控制項。 特殊功能<xref:System.Windows.Forms.StatusStrip>包括自訂資料表配置、 支援表單的大小和移動盡辦法，而`Spring`屬性，可讓<xref:System.Windows.Forms.ToolStripStatusLabel>自動填滿可用空間。  
  
 下列項目專為緊密地與這兩個<xref:System.Windows.Forms.ToolStripSystemRenderer>和<xref:System.Windows.Forms.ToolStripProfessionalRenderer>中所有方向。 它們是在設計階段的預設可用的<xref:System.Windows.Forms.StatusStrip>控制項：  
  
-   <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### <a name="contextmenustrip"></a>ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenuStrip>取代<xref:System.Windows.Forms.ContextMenu>。 您可以將關聯<xref:System.Windows.Forms.ContextMenuStrip>與任何控制項，以滑鼠右鍵按一下自動顯示內容功能表 （或快顯功能表）。 您可以顯示<xref:System.Windows.Forms.ContextMenuStrip>以程式設計方式利用<xref:System.Windows.Forms.ToolStripDropDown.Show%2A>方法。 <xref:System.Windows.Forms.ContextMenuStrip>支援可取消<xref:System.Windows.Forms.ToolStripDropDown.Opening>和<xref:System.Windows.Forms.ToolStripDropDown.Closing>處理動態擴展和多個按一下案例的事件。 <xref:System.Windows.Forms.ContextMenuStrip>支援影像、 功能表項目檢查狀態、 文字、 存取金鑰、 捷徑和串聯功能表。  
  
 下列項目專為緊密地與這兩個<xref:System.Windows.Forms.ToolStripSystemRenderer>和<xref:System.Windows.Forms.ToolStripProfessionalRenderer>中所有方向。 它們是在設計階段的預設可用的<xref:System.Windows.Forms.ContextMenuStrip>控制項：  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="toolstrip-generic-features"></a>ToolStrip 一般功能  
 下列主題將描述功能和行為的一般至<xref:System.Windows.Forms.ToolStrip>和衍生的控制項。  
  
#### <a name="painting"></a>繪製  
 您可以在中執行自訂繪製<xref:System.Windows.Forms.ToolStrip>數種方式的控制項。 如同其他 Windows Form 控制項，<xref:System.Windows.Forms.ToolStrip>和<xref:System.Windows.Forms.ToolStripItem>都具有可覆寫`OnPaint`方法和`Paint`事件。 規則的繪製，座標系統是控制項的相對於用戶端區域。也就是控制項的左上角為 0，0。 `Paint`事件和`OnPaint`方法<xref:System.Windows.Forms.ToolStripItem>行為與其他控制項的繪製事件一樣。  
  
 <xref:System.Windows.Forms.ToolStrip>控制項也會提供更精細的存取權的項目和容器透過轉譯<xref:System.Windows.Forms.ToolStripRenderer>類別，具有可覆寫繪製背景、 項目背景、 項目影像、 項目箭號、 項目文字的方法，以及框線<xref:System.Windows.Forms.ToolStrip>. 這些方法的事件引數會公開數個屬性，例如矩形、 色彩和文字格式，您可以視需要進行調整。  
  
 若要調整幾個層面的項目繪製的方式，您通常會覆寫<xref:System.Windows.Forms.ToolStripRenderer>。  
  
 如果您要撰寫新的項目，且想要控制繪製的所有層面，覆寫`OnPaint`方法。 從`OnPaint`，您可以使用從方法<xref:System.Windows.Forms.ToolStripRenderer>。  
  
 根據預設，<xref:System.Windows.Forms.ToolStrip>為雙重緩衝，利用<xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer>設定。  
  
#### <a name="parenting"></a>父代  
 容器的擁有權和父代的概念是更為複雜的<xref:System.Windows.Forms.ToolStrip>控制項比其他 Windows Form 容器控制項。 是為了支援動態案例，例如溢位，跨多個共用下拉式項目<xref:System.Windows.Forms.ToolStrip>項目，以及支援產生<xref:System.Windows.Forms.ContextMenuStrip>的控制項。  
  
 下列清單描述與父代相關的成員，並說明其用法。  
  
-   <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A>存取的項目是下拉式清單項目的來源。 這是類似於<xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>，而不是傳回的控制項，它會傳回但<xref:System.Windows.Forms.ToolStripItem>。  
  
-   <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>判斷哪些控制項來源的<xref:System.Windows.Forms.ContextMenuStrip>當多個控制項共用相同<xref:System.Windows.Forms.ContextMenuStrip>。  
  
-   <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A>是唯讀的存取子，來<xref:System.Windows.Forms.ToolStripItem.Parent%2A>屬性。 父代與擁有者的父代表示傳回的目前<xref:System.Windows.Forms.ToolStrip>項目顯示，這可能會溢位區域。  
  
-   <xref:System.Windows.Forms.ToolStripItem.Owner%2A>傳回<xref:System.Windows.Forms.ToolStrip>的項目集合會包含目前<xref:System.Windows.Forms.ToolStripItem>。 這是最佳的方式來參考<xref:System.Windows.Forms.ToolStrip.ImageList%2A>或其他內容，在最上層<xref:System.Windows.Forms.ToolStrip>而不需要撰寫特殊的程式碼來處理溢位。  
  
#### <a name="behavior-of-inherited-controls"></a>繼承的控制項的行為  
 它們用在繼承時，會鎖定下列控制項：  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.ToolStripPanel>其中包含中的面板<xref:System.Windows.Forms.ToolStripContainer>和也個別<xref:System.Windows.Forms.ToolStripPanel>控制項。  
  
 例如，使用上述清單中的一或多個控制項建立新的 Windows Form 應用程式。 設定一或多個控制項的存取修飾詞`public`或`protected`，然後建置專案。 加入繼承自第一個表單，表單，然後選取 繼承的控制項。 該控制項會出現鎖定，其運作方式如同其存取修飾詞是`private`。  
  
#### <a name="toolstripcontainer-support-of-inheritance"></a>ToolStripContainer 的繼承的支援  
 <xref:System.Windows.Forms.ToolStripContainer>控制項支援少數繼承情況下，下列範例類似：  
  
1.  新建 Windows Forms 應用程式  
  
2.  將 <xref:System.Windows.Forms.ToolStripContainer> 加入表單。  
  
3.  設定的存取修飾詞<xref:System.Windows.Forms.ToolStripContainer>至`public`或`protected`。  
  
4.  新增的任何組合<xref:System.Windows.Forms.ToolStrip>， <xref:System.Windows.Forms.MenuStrip>，和<xref:System.Windows.Forms.ContextMenuStrip>控制項<xref:System.Windows.Forms.ToolStripPanel>的區域<xref:System.Windows.Forms.ToolStripContainer>。  
  
5.  建置專案。  
  
6.  加入繼承自第一個表單的表單。  
  
7.  選取 繼承<xref:System.Windows.Forms.ToolStripContainer>表單上。  
  
#### <a name="inherited-behavior-of-child-controls"></a>子控制項的繼承的行為  
 完成上述步驟之後，就會發生下列繼承的行為：  
  
-   在設計師中，控制項就會出現以繼承的圖示。  
  
-   <xref:System.Windows.Forms.ToolStripPanel>控制項已被鎖定，因此您無法選取或重新排列其內容。  
  
-   您可以將控制項加入<xref:System.Windows.Forms.ToolStripContentPanel>移動控制項，讓它們的子控制項<xref:System.Windows.Forms.ToolStripContentPanel>。  
  
-   建立表單之後，您的變更保存。  
  
    > [!NOTE]
    >  移除所有的存取修飾詞<xref:System.Windows.Forms.ToolStripPanel>控制項屬於<xref:System.Windows.Forms.ToolStripContainer>。 存取修飾詞<xref:System.Windows.Forms.ToolStripContainer>控管整個控制項。  
  
#### <a name="partial-trust"></a>部分信任  
 限制`ToolStrip`s 在部分信任下的專為避免不小心的項目可能會使用未經授權的人員或服務的個人資訊。 保護措施如下所示：  
  
-   `ToolStripDropDown`控制項需要<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>顯示中的項目<xref:System.Windows.Forms.ToolStripControlHost>。 這適用於兩個內建控制項例如<xref:System.Windows.Forms.ToolStripTextBox>， <xref:System.Windows.Forms.ToolStripComboBox>，和<xref:System.Windows.Forms.ToolStripProgressBar>也是用來建立使用者控制項。 如果不符合此需求，將不會顯示這些項目。 不會有例外狀況擲回。  
  
-   設定<xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A>屬性`false`不允許，和可取消<xref:System.Windows.Forms.ToolStripDropDown.Closing>事件參數已忽略。 這可讓多個按鍵輸入而不解除下拉式項目。 如果不符合此需求，將不會顯示此類項目。 不會有例外狀況擲回。  
  
-   如果它們發生在部分信任的內容以外，不會引發許多處理事件的按鍵輸入<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>。  
  
-   存取索引鍵不是處理時<xref:System.Security.Permissions.UIPermissionWindow.AllWindows>未授與。  
  
#### <a name="usage"></a>使用方式  
 下列的使用模式有並無影響<xref:System.Windows.Forms.ToolStrip>版面配置、 鍵盤互動和使用者行為：  
  
-   在中聯結<xref:System.Windows.Forms.ToolStripPanel>  
  
     <xref:System.Windows.Forms.ToolStrip>可以內重新定位<xref:System.Windows.Forms.ToolStripPanel>和透過<xref:System.Windows.Forms.ToolStripPanel>s。 `Dock`屬性會被忽略，而且如果<xref:System.Windows.Forms.ToolStrip.Stretch%2A>屬性是`false`，大小為<xref:System.Windows.Forms.ToolStrip>中加入項目會隨著<xref:System.Windows.Forms.ToolStripPanel>。 一般而言，<xref:System.Windows.Forms.ToolStrip>不會參與的索引標籤順序。  
  
-   已停駐  
  
     <xref:System.Windows.Forms.ToolStrip>放一邊的容器中的固定位置，而其大小會展開整個停駐的邊緣上方。 一般而言，<xref:System.Windows.Forms.ToolStrip>不會參與的索引標籤順序。  
  
-   絕對位置  
  
     <xref:System.Windows.Forms.ToolStrip>是如同其他控制項，它由放<xref:System.Windows.Forms.Control.Location%2A>屬性有固定的大小，和通常參與的索引標籤順序。  
  
#### <a name="keyboard-interaction"></a>鍵盤互動  
  
##### <a name="access-keys"></a>便捷鍵  
 結合使用，或 ALT 鍵之後，存取金鑰是一種方式啟動控制項，使用鍵盤。 <xref:System.Windows.Forms.ToolStrip>支援兩個明確和隱含的存取金鑰。 連字號 (&) 字元前面的字母，則會使用明確的定義。 隱含定義使用的演算法會嘗試尋找相符的項目，根據順序中的字元的指定`Text`屬性。  
  
##### <a name="shortcut-keys"></a>快速鍵  
 所使用的快速鍵<xref:System.Windows.Forms.MenuStrip>使用的組合<xref:System.Windows.Forms.Keys>列舉型別 （這不是特定的順序） 來定義的快速鍵。 您也可以使用<xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A>屬性以顯示快速鍵的文字，例如顯示"Del"，而不 「 刪除 」。  
  
##### <a name="navigation"></a>巡覽  
 ALT 鍵會啟動<xref:System.Windows.Forms.MenuStrip>指向<xref:System.Windows.Forms.Form.MainMenuStrip%2A>。 從該處，CTRL + TAB 之間的巡覽<xref:System.Windows.Forms.ToolStrip>內控制`ToolStripPanel`s。 中的項目之間巡覽的 TAB 鍵和數字鍵台上的方向鍵<xref:System.Windows.Forms.ToolStrip>。 特殊的演算法可處理導覽溢位區域中。 空格鍵選取<xref:System.Windows.Forms.ToolStripButton>， <xref:System.Windows.Forms.ToolStripDropDownButton>，或<xref:System.Windows.Forms.ToolStripSplitButton>。  
  
##### <a name="focus-and-validation"></a>焦點和驗證  
 ALT 鍵，以啟動時<xref:System.Windows.Forms.MenuStrip>或<xref:System.Windows.Forms.ToolStrip>通常都不需要也不移除從目前擁有焦點的控制項焦點。 如果沒有內裝載的控制項<xref:System.Windows.Forms.MenuStrip> 下拉式清單或<xref:System.Windows.Forms.MenuStrip>，控制項取得焦點，當使用者按下 TAB 鍵。 一般情況下， <xref:System.Windows.Forms.Control.GotFocus>， <xref:System.Windows.Forms.Control.LostFocus>， <xref:System.Windows.Forms.Control.Enter>，和<xref:System.Windows.Forms.Control.Leave>事件<xref:System.Windows.Forms.MenuStrip>可能不在由鍵盤啟用時才引發。 在這種情況下，使用<xref:System.Windows.Forms.MenuStrip.MenuActivate>和<xref:System.Windows.Forms.MenuStrip.MenuDeactivate>事件改為。  
  
 根據預設，<xref:System.Windows.Forms.ToolStrip.CausesValidation%2A>是`false`。 呼叫<xref:System.Windows.Forms.ContainerControl.Validate%2A>明確上執行驗證的表單。  
  
#### <a name="layout"></a>配置  
 您可以控制<xref:System.Windows.Forms.ToolStrip>版面配置選擇其中一個成員<xref:System.Windows.Forms.ToolStripLayoutStyle>與<xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A>屬性。  
  
##### <a name="stack-layouts"></a>堆疊配置  
 「 堆疊 」 是在兩端的項目旁邊彼此排列<xref:System.Windows.Forms.ToolStrip>。 下列清單描述堆疊配置。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow> 是預設值。 這項設定會導致<xref:System.Windows.Forms.ToolStrip>改變它自動在按照所使用的版面配置<xref:System.Windows.Forms.ToolStrip.Orientation%2A>屬性來處理拖曳和停駐的案例。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>呈現<xref:System.Windows.Forms.ToolStrip>旁邊彼此垂直項目。  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow>呈現<xref:System.Windows.Forms.ToolStrip>旁邊彼此水平項目。  
  
##### <a name="other-features-of-stack-layouts"></a>堆疊配置的其他功能  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A>決定結尾<xref:System.Windows.Forms.ToolStrip>以項目對齊。  
  
 當項目無法納入<xref:System.Windows.Forms.ToolStrip>，溢位按鈕就會自動出現。 <xref:System.Windows.Forms.ToolStripItem.Overflow%2A>屬性設定會決定項目是否要出現在溢位區域一律，如有需要或永遠不會。  
  
 在<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>事件，您可以檢查<xref:System.Windows.Forms.ToolStripItem.Placement%2A>屬性來判斷項目是否已放在主要<xref:System.Windows.Forms.ToolStrip>，溢位<xref:System.Windows.Forms.ToolStrip>，或如果它目前未顯示完全。 項目不會顯示原因的常見原因是此項目，不適合在主要<xref:System.Windows.Forms.ToolStrip>及其<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>屬性設定為<xref:System.Windows.Forms.ToolStripItemOverflow.Never>。  
  
 請<xref:System.Windows.Forms.ToolStrip>可移動放入<xref:System.Windows.Forms.ToolStripPanel>並設定其<xref:System.Windows.Forms.ToolStrip.GripStyle%2A>至<xref:System.Windows.Forms.ToolStripGripStyle.Visible>。  
  
##### <a name="other-layout-options"></a>其他版面配置選項  
 其他版面配置選項<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>和<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>。  
  
##### <a name="flow-layout"></a>流程配置  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>版面配置是預設值為<xref:System.Windows.Forms.ContextMenuStrip>， <xref:System.Windows.Forms.ToolStripDropDownMenu>，和<xref:System.Windows.Forms.ToolStripOverflow>。 類似於<xref:System.Windows.Forms.FlowLayoutPanel>。 功能<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>配置如下：  
  
-   所有功能<xref:System.Windows.Forms.FlowLayoutPanel>由公開<xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>屬性。 您必須轉換<xref:System.Windows.Forms.LayoutSettings>類別<xref:System.Windows.Forms.FlowLayoutSettings>類別。  
  
-   您可以使用<xref:System.Windows.Forms.ToolStripItem.Dock%2A>和<xref:System.Windows.Forms.ToolStripItem.Anchor%2A>對齊的項目在資料列中的程式碼中的屬性。  
  
-   忽略 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 屬性。  
  
-   在<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>事件，您可以檢查<xref:System.Windows.Forms.ToolStripItem.Placement%2A>屬性來判斷項目是否已放在主要<xref:System.Windows.Forms.ToolStrip>或不適用。  
  
-   底框不會呈現，因此<xref:System.Windows.Forms.ToolStrip>中<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>中的配置樣式<xref:System.Windows.Forms.ToolStripPanel>無法移動。  
  
-   <xref:System.Windows.Forms.ToolStrip>溢位按鈕時，不會轉譯和<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>會被忽略。  
  
##### <a name="table-layout"></a>資料表配置  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>版面配置是預設值為<xref:System.Windows.Forms.StatusStrip>。 類似於<xref:System.Windows.Forms.TableLayoutPanel>。 功能<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>配置如下：  
  
-   所有功能<xref:System.Windows.Forms.TableLayoutPanel>由公開<xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A>屬性。 您必須轉換<xref:System.Windows.Forms.LayoutSettings>類別<xref:System.Windows.Forms.TableLayoutSettings>類別。  
  
-   您可以使用<xref:System.Windows.Forms.ToolStripItem.Dock%2A>和<xref:System.Windows.Forms.ToolStripItem.Anchor%2A>對齊的項目與資料表資料格內的程式碼中的屬性。  
  
-   忽略 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> 屬性。  
  
-   在<xref:System.Windows.Forms.ToolStrip.LayoutCompleted>事件，您可以檢查<xref:System.Windows.Forms.ToolStripItem.Placement%2A>屬性來判斷項目是否已放在主要<xref:System.Windows.Forms.ToolStrip>或不適用。  
  
-   底框不會呈現，因此<xref:System.Windows.Forms.ToolStrip>中<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>中的配置樣式<xref:System.Windows.Forms.ToolStripPanel>無法移動。  
  
-   <xref:System.Windows.Forms.ToolStrip>溢位按鈕時，不會轉譯和<xref:System.Windows.Forms.ToolStripItem.Overflow%2A>會被忽略。  
  
## <a name="toolstripitem"></a>ToolStripItem  
 下列主題將描述<xref:System.Windows.Forms.ToolStripItem>和從它衍生的控制項。  
  
 <xref:System.Windows.Forms.ToolStripItem>移入的所有項目的抽象基底類別<xref:System.Windows.Forms.ToolStrip>。 下列物件模型顯示<xref:System.Windows.Forms.ToolStripItem>繼承階層架構。  
  
 ![ToolStripItem 物件模型](../../../../docs/framework/winforms/controls/media/toolstripitemobjectmodel.gif "ToolStripItemObjectModel")  
ToolStripItem 物件模型  
  
 <xref:System.Windows.Forms.ToolStripItem>類別是直接繼承自<xref:System.Windows.Forms.ToolStripItem>，或它們間接繼承自<xref:System.Windows.Forms.ToolStripItem>透過<xref:System.Windows.Forms.ToolStripControlHost>或<xref:System.Windows.Forms.ToolStripDropDownItem>。  
  
 <xref:System.Windows.Forms.ToolStripItem>控制項必須包含在<xref:System.Windows.Forms.ToolStrip>， <xref:System.Windows.Forms.MenuStrip>， <xref:System.Windows.Forms.StatusStrip>，或<xref:System.Windows.Forms.ContextMenuStrip>並無法直接加入至表單。 不同的容器類別設計成包含適當的子集<xref:System.Windows.Forms.ToolStripItem>控制項。  
  
 下表列出內建<xref:System.Windows.Forms.ToolStripItem>控制項和看起來最佳的容器。 雖然任何<xref:System.Windows.Forms.ToolStrip>項目可以裝載於任何<xref:System.Windows.Forms.ToolStrip>-衍生的容器，這些項目都是設計來尋找最佳下列容器中：  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripDropDown>不會顯示在設計工具的工具箱。  
  
|包含的項目|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|  
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|  
|<xref:System.Windows.Forms.ToolStripButton>|是|否|否|否|是|  
|<xref:System.Windows.Forms.ToolStripComboBox>|是|是|是|否|是|  
|<xref:System.Windows.Forms.ToolStripSplitButton>|是|否|否|是|是|  
|<xref:System.Windows.Forms.ToolStripLabel>|是|否|否|是|是|  
|<xref:System.Windows.Forms.ToolStripSeparator>|是|是|是|否|是|  
|<xref:System.Windows.Forms.ToolStripDropDownButton>|是|否|否|是|是|  
|<xref:System.Windows.Forms.ToolStripTextBox>|是|是|是|否|是|  
|<xref:System.Windows.Forms.ToolStripMenuItem>|否|是|是|否|否|  
|<xref:System.Windows.Forms.ToolStripStatusLabel>|否|否|否|是|否|  
|<xref:System.Windows.Forms.ToolStripProgressBar>|是|否|否|是|否|  
|<xref:System.Windows.Forms.ToolStripControlHost>|是|是|否|是|是|  
  
### <a name="toolstripbutton"></a>ToolStripButton  
 <xref:System.Windows.Forms.ToolStripButton>按鈕項目<xref:System.Windows.Forms.ToolStrip>。 您可以使用各種框線樣式，其顯示，您可以使用它來代表，並啟用的操作狀態。 您也可以定義為預設有焦點。  
  
### <a name="toolstriplabel"></a>ToolStripLabel  
 <xref:System.Windows.Forms.ToolStripLabel>標籤在提供的功能<xref:System.Windows.Forms.ToolStrip>控制項。 <xref:System.Windows.Forms.ToolStripLabel>就像是<xref:System.Windows.Forms.ToolStripButton>，不會根據預設取得焦點和，不會呈現為推入或反白顯示。  
  
 <xref:System.Windows.Forms.ToolStripLabel>當主控項目的支援便捷鍵。  
  
 使用<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>， <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>，和<xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A>屬性<xref:System.Windows.Forms.ToolStripLabel>支援中的連結控制<xref:System.Windows.Forms.ToolStrip>。  
  
### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel>版本<xref:System.Windows.Forms.ToolStripLabel>專為使用中設計<xref:System.Windows.Forms.StatusStrip>。 特殊功能包括<xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>， <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>，和<xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>。  
  
### <a name="toolstripseparator"></a>ToolStripSeparator  
 <xref:System.Windows.Forms.ToolStripSeparator>將垂直或水平列加入至工具列或功能表上，視方向而定。 它提供的群組或項目，例如功能表上的區別。  
  
 您可以加入<xref:System.Windows.Forms.ToolStripSeparator>在設計階段，從下拉式清單選擇。 不過，您可以也會自動建立<xref:System.Windows.Forms.ToolStripSeparator>輸入連字號 （-） 設計工具的範本 節點中，或在<xref:System.Windows.Forms.ToolStripItemCollection.Add%2A>方法。  
  
### <a name="toolstripcontrolhost"></a>ToolStripControlHost  
 <xref:System.Windows.Forms.ToolStripControlHost>是抽象的基底類別，如<xref:System.Windows.Forms.ToolStripComboBox>， <xref:System.Windows.Forms.ToolStripTextBox>，和<xref:System.Windows.Forms.ToolStripProgressBar>。 <xref:System.Windows.Forms.ToolStripControlHost>裝載其他控制項，包括自訂控制項，有兩種：  
  
-   建構<xref:System.Windows.Forms.ToolStripControlHost>與衍生自類別<xref:System.Windows.Forms.Control>。 若要完整存取裝載的控制項和屬性，您必須轉換<xref:System.Windows.Forms.ToolStripControlHost.Control%2A>回到實際屬性類別它代表。  
  
-   擴充<xref:System.Windows.Forms.ToolStripControlHost>，並繼承的類別預設建構函式中呼叫基底類別建構函式的類別衍生自傳遞<xref:System.Windows.Forms.Control>。 此選項可讓您包裝通用控制項的方法和屬性中的輕鬆存取<xref:System.Windows.Forms.ToolStrip>。  
  
### <a name="toolstripcombobox"></a>ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox>是<xref:System.Windows.Forms.ComboBox>適合裝載在<xref:System.Windows.Forms.ToolStrip>。 裝載的控制項的屬性和事件的子集會公開在<xref:System.Windows.Forms.ToolStripComboBox>層級，但基礎<xref:System.Windows.Forms.ComboBox>控制項是完全可透過存取<xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A>屬性。  
  
### <a name="toolstriptextbox"></a>ToolStripTextBox  
 <xref:System.Windows.Forms.ToolStripTextBox>是<xref:System.Windows.Forms.TextBox>適合裝載在<xref:System.Windows.Forms.ToolStrip>。 裝載的控制項的屬性和事件的子集會公開在<xref:System.Windows.Forms.ToolStripTextBox>層級，但基礎<xref:System.Windows.Forms.TextBox>控制項是完全可透過存取<xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A>屬性。  
  
### <a name="toolstripprogressbar"></a>ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar>是<xref:System.Windows.Forms.ProgressBar>適合裝載在<xref:System.Windows.Forms.ToolStrip>。 裝載的控制項的屬性和事件的子集會公開在<xref:System.Windows.Forms.ToolStripProgressBar>層級，但基礎<xref:System.Windows.Forms.ProgressBar>控制項是完全可透過存取<xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A>屬性。  
  
### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem>是抽象的基底類別，如<xref:System.Windows.Forms.ToolStripMenuItem>， <xref:System.Windows.Forms.ToolStripDropDownButton>，和<xref:System.Windows.Forms.ToolStripSplitButton>，它可以裝載項目直接或主機的下拉式清單的容器中的其他項目。 您可以設定<xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A>屬性<xref:System.Windows.Forms.ToolStripDropDown>和設定<xref:System.Windows.Forms.ToolStrip.Items%2A>屬性<xref:System.Windows.Forms.ToolStripDropDown>。 存取這些下拉式清單項目直接透過<xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A>屬性。  
  
### <a name="toolstripmenuitem"></a>在 toolstripmenuitem 中  
 <xref:System.Windows.Forms.ToolStripMenuItem>是<xref:System.Windows.Forms.ToolStripDropDownItem>適用於<xref:System.Windows.Forms.ToolStripDropDownMenu>和<xref:System.Windows.Forms.ContextMenuStrip>處理功能表的特殊反白顯示、 配置和資料行排列。  
  
### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton>看起來像<xref:System.Windows.Forms.ToolStripButton>，但是當使用者按一下它，它會顯示下拉式區域。 隱藏或顯示的下拉式箭號，藉由設定<xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A>屬性。 <xref:System.Windows.Forms.ToolStripDropDownButton>主機<xref:System.Windows.Forms.ToolStripOverflowButton>顯示溢位的項目<xref:System.Windows.Forms.ToolStrip>。  
  
### <a name="toolstripsplitbutton"></a>ToolStripSplitButton  
 <xref:System.Windows.Forms.ToolStripSplitButton>將按鈕和下拉式按鈕的功能。  
  
 使用<xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A>同步的屬性<xref:System.Windows.Forms.Control.Click>與按鈕上顯示的項目所選擇的下拉式清單項目的事件。  
  
### <a name="toolstripitem-generic-features"></a>ToolStripItem 一般功能  
 <xref:System.Windows.Forms.ToolStripItem>提供下列一般功能和選項，以繼承的控制項：  
  
-   核心事件  
  
-   處理影像  
  
-   對齊方式  
  
-   文字和影像的關聯性  
  
-   顯示樣式  
  
#### <a name="core-events"></a>核心事件  
 <xref:System.Windows.Forms.ToolStripItem>控制項收到自己按一下、 滑鼠及繪畫事件，而且可以執行前置處理也有些鍵盤。  
  
#### <a name="image-handling"></a>處理影像  
 <xref:System.Windows.Forms.ToolStripItem.Image%2A>， <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>， <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>， <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>，和<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A>屬性屬於映像處理的各個層面。 使用中的映像<xref:System.Windows.Forms.ToolStrip>控制項設定這些屬性直接或藉由設定執行時間-僅限<xref:System.Windows.Forms.ToolStrip.ImageList%2A>屬性。  
  
 影像縮放比例取決於屬性中的互動<xref:System.Windows.Forms.ToolStrip>和<xref:System.Windows.Forms.ToolStripItem>、，如下所示：  
  
-   <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A>小數位數的映像的組合所決定最終映像<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A>設定和容器的<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>設定。  
  
    -   如果<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>是`true`（預設值） 和<xref:System.Windows.Forms.ToolStripItemImageScaling>是<xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>，沒有影像的縮放比例就會發生，而<xref:System.Windows.Forms.ToolStrip>大小是最大的項目或指定的最小大小。  
  
    -   如果<xref:System.Windows.Forms.ToolStrip.AutoSize%2A>是`false`和<xref:System.Windows.Forms.ToolStripItemImageScaling>是<xref:System.Windows.Forms.ToolStripItemImageScaling.None>，都沒有映像，也不<xref:System.Windows.Forms.ToolStrip>調整，就會發生。  
  
#### <a name="alignment"></a>對齊方式  
 值<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>屬性會決定結尾<xref:System.Windows.Forms.ToolStrip>在出現的項目。 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A>屬性的運作方式時，才的配置樣式<xref:System.Windows.Forms.ToolStrip>設為其中一個堆疊溢位值。  
  
 項目會置於<xref:System.Windows.Forms.ToolStrip>中之項目的項目集合中出現的順序。 若要以程式設計方式變更項目已配置版面、 使用<xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A>方法來移動項目集合中。 這個方法會移動的項目，但不會複製。  
  
#### <a name="text-and-image-relationship"></a>文字和影像關聯性  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A>屬性會定義文字與影像的相對位置上<xref:System.Windows.Forms.ToolStripItem>。 缺少影像、 文字或這兩項目會被視為特殊案例，讓<xref:System.Windows.Forms.ToolStripItem>不會顯示空白的位置，針對遺漏的項目或項目。  
  
#### <a name="display-style"></a>顯示樣式  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>可讓您同時顯示只有您想要設定的項目 Text 和 Image 屬性的值。 這通常用來在不同的內容中顯示相同的項目時會變更顯示樣式。  
  
## <a name="accessory-classes"></a>附屬類別  
 類別可提供各種其他功能包括：  
  
-   <xref:System.Windows.Forms.ToolStripManager>支援<xref:System.Windows.Forms.ToolStrip>-相關工作的整個應用程式，例如合併、 設定以及轉譯器的選項。  
  
-   <xref:System.Windows.Forms.ToolStripRenderer>可讓您套用特定樣式或佈景主題到<xref:System.Windows.Forms.ToolStrip>輕鬆。  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer>建立畫筆和筆刷色彩可取代資料表為基礎 (<xref:System.Windows.Forms.ProfessionalColorTable>)。  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer>適用於系統色彩和單層視覺化樣式<xref:System.Windows.Forms.ToolStrip>應用程式。  
  
-   <xref:System.Windows.Forms.ToolStripContainer>類似於<xref:System.Windows.Forms.SplitContainer>。 它會使用四個停駐的側邊面板 (的執行個體<xref:System.Windows.Forms.ToolStripPanel>) 和一個中央面板 (執行個體<xref:System.Windows.Forms.ToolStripContentPanel>) 來建立一般的排列方式。 您無法移除側邊面板中，但您可以隱藏起來。 您不可以移除或隱藏中間的面板。 您可以使用一或多個排列<xref:System.Windows.Forms.ToolStrip>， <xref:System.Windows.Forms.MenuStrip>，或<xref:System.Windows.Forms.StatusStrip>側邊面板中，而且您的控制項可用於其他控制項的中央面板。 <xref:System.Windows.Forms.ToolStripContentPanel>也可用來取得轉譯器支援為一致的外觀的表單的本文。 <xref:System.Windows.Forms.ToolStripContainer>不支援多重文件介面 (MDI)。  
  
-   <xref:System.Windows.Forms.ToolStripPanel>提供位置來移動和排列<xref:System.Windows.Forms.ToolStrip>控制項。 如果您選擇這樣做，可以使用只有一個面板和<xref:System.Windows.Forms.ToolStripPanel>在 MDI 狀況下順利運作。  
  
## <a name="see-also"></a>另請參閱  
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [ToolStrip 技術摘要](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)  
 [ToolStrip 控制項](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [MenuStrip 控制項](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [StatusStrip 控制項](../../../../docs/framework/winforms/controls/statusstrip-control.md)  
 [ContextMenuStrip 控制項](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)  
 [BindingNavigator 控制項](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
