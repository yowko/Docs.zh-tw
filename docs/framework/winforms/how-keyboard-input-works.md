---
title: 鍵盤輸入的運作方式
ms.date: 03/30/2017
helpviewer_keywords:
- keyboard input [Windows Forms], about keyboard input
- keyboards [Windows Forms], keyboard input
- Windows Forms, keyboard input
ms.assetid: 9a29433c-a180-49bb-b74c-d187786584c8
ms.openlocfilehash: 4335798395a3b73dbcb2546a6fadac3d8efedb64
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204740"
---
# <a name="how-keyboard-input-works"></a>鍵盤輸入的運作方式
Windows Forms 會引發鍵盤事件以回應 Windows 訊息，進而處理鍵盤輸入。 大部分的 Windows Forms 應用程式會藉由處理鍵盤事件來處理鍵盤輸入。 不過，您需要了解鍵盤訊息的運作方式，以便實作更進階的鍵盤輸入案例，例如在按鍵觸達控制項之前先行攔截。 本主題說明 Windows Forms 可辨識的按鍵資料類型，並提供鍵盤訊息的路由方式概觀。 如需鍵盤事件的相關資訊，請參閱[使用鍵盤事件](using-keyboard-events.md)。  
  
## <a name="types-of-keys"></a>按鍵類型  
 Windows Form 識別為表示的位元虛擬按鍵碼的鍵盤輸入<xref:System.Windows.Forms.Keys>列舉型別。 使用<xref:System.Windows.Forms.Keys>列舉型別，您可以結合一系列的已按下按鍵來產生單一值。 這些值對應於伴隨 WM_KEYDOWN 和 WM_SYSKEYDOWN Windows 訊息的值。 您可以藉由處理來偵測大多數實體按鍵<xref:System.Windows.Forms.Control.KeyDown>或<xref:System.Windows.Forms.Control.KeyUp>事件。 字元按鍵是子集<xref:System.Windows.Forms.Keys>列舉型別，並對應至伴隨 WM_CHAR 和 WM_SYSCHAR Windows 訊息的值。 如果已按下按鍵的組合產生一個字元，您可以藉由處理來偵測字元<xref:System.Windows.Forms.Control.KeyPress>事件。 或者，您可以使用<xref:Microsoft.VisualBasic.Devices.Keyboard>Visual Basic 程式設計介面，以探索哪些按鍵已按下及傳送按鍵所公開。 如需詳細資訊，請參閱[存取鍵盤](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)。  
  
## <a name="order-of-keyboard-events"></a>鍵盤事件的順序  
 如先前所列，控制項上可能發生有 3 鍵盤相關事件。 下列序列顯示事件的一般順序︰  
  
1.  使用者按"a"鍵、 索引鍵會經過前置處理、 分派，並有<xref:System.Windows.Forms.Control.KeyDown>就會發生事件。  
  
2.  使用者按住"a"鍵、 索引鍵會經過前置處理、 分派，並有<xref:System.Windows.Forms.Control.KeyPress>就會發生事件。  
  
     當使用者按住一個按鍵時，此事件會發生很多次。  
  
3.  使用者放開"a"鍵，此鍵會經過前置處理、 分派和<xref:System.Windows.Forms.Control.KeyUp>就會發生事件。  
  
## <a name="preprocessing-keys"></a>按鍵前置處理  
 如同其他訊息，在處理鍵盤訊息<xref:System.Windows.Forms.Control.WndProc%2A>表單或控制項的方法。 不過，在鍵盤之前處理訊息，<xref:System.Windows.Forms.Control.PreProcessMessage%2A>方法會呼叫可覆寫以處理特殊字元按鍵與實體索引鍵的一或多個方法。 您可以覆寫這些方法，以在控制項處理訊息之前，先偵測並篩選特定按鍵。 下表顯示正在執行的動作以及發生的相關方法 (依方法的發生順序顯示)。  
  
### <a name="preprocessing-for-a-keydown-event"></a>KeyDown 事件前置處理  
  
|動作|相關方法|注意|  
|------------|--------------------|-----------|  
|檢查命令按鍵，例如快速鍵或功能表捷徑。|<xref:System.Windows.Forms.Control.ProcessCmdKey%2A>|這個方法會處理命令按鍵，其優先於一般按鍵。 如果此方法傳回 `true`，就不會發送按鍵訊息，也不會發生按鍵事件。 如果它傳回`false`，<xref:System.Windows.Forms.Control.IsInputKey%2A>稱為`.`|  
|檢查需要前置處理的特殊按鍵或應該引發的標準字元按鍵<xref:System.Windows.Forms.Control.KeyDown>事件並分派至控制項。|<xref:System.Windows.Forms.Control.IsInputKey%2A>|如果此方法會傳回`true`，表示控制項是一般字元和<xref:System.Windows.Forms.Control.KeyDown>就會引發事件。 如果`false`，<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>呼叫。 **注意：** 若要確保控制項取得索引鍵或索引鍵的組合，您可以處理<xref:System.Windows.Forms.Control.PreviewKeyDown>事件和 set<xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A>的<xref:System.Windows.Forms.PreviewKeyDownEventArgs>到`true`針對您想要的索引鍵。|  
|檢查導覽鍵 (ESC、TAB、Return 或方向鍵)。|<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|這個方法會處理運用控制項內特殊功能的實體按鍵，例如在控制項與其父代之間切換焦點。 如果立即的控制項不會處理索引鍵， <xref:System.Windows.Forms.Control.ProcessDialogKey%2A> ，以此類推到階層中的最上層控制項的父控制項上呼叫。 如果此方法傳回 `true`，則已完成前置處理，而不會產生按鍵事件。 如果它傳回`false`、<xref:System.Windows.Forms.Control.KeyDown>就會發生事件。|  
  
### <a name="preprocessing-for-a-keypress-event"></a>KeyPress 事件前置處理  
  
|動作|相關方法|注意|  
|------------|--------------------|-----------|  
|查看按鍵是否為應由控制項處理的標準字元|<xref:System.Windows.Forms.Control.IsInputChar%2A>|如果字元是一般字元，則這個方法會傳回`true`，則<xref:System.Windows.Forms.Control.KeyPress>就會引發事件，並沒有進一步的前置處理，就會發生。 否則<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>將呼叫。|  
|查看此字元是否為助憶鍵 (例如按鈕上 &OK)|<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|這個方法類似於<xref:System.Windows.Forms.Control.ProcessDialogKey%2A>，將會呼叫控制項階層架構。 如果控制項是容器控制項，它會檢查助憶鍵藉由呼叫<xref:System.Windows.Forms.Control.ProcessMnemonic%2A>對本身與其子控制項。 如果<xref:System.Windows.Forms.Control.ProcessDialogChar%2A>會傳回`true`、<xref:System.Windows.Forms.Control.KeyPress>事件不會發生。|  
  
## <a name="processing-keyboard-messages"></a>處理鍵盤訊息  
 鍵盤訊息到達之後<xref:System.Windows.Forms.Control.WndProc%2A>方法的表單或控制項，便會處理一組可覆寫的方法。 每一種方法會傳回<xref:System.Boolean>指定鍵盤訊息是否已處理和控制項所使用的值。 如果其中一個方法傳回 `true`，則會將訊息視為已處理，而不會傳遞給控制項的基底或父代做進一步處理。 否則，訊息會留在訊息佇列中，而且可能會由控制項的基底或父代中的另一個方法所處理。 下表顯示處理鍵盤訊息的方法。  
  
|方法|注意|  
|------------|-----------|  
|<xref:System.Windows.Forms.Control.ProcessKeyMessage%2A>|這個方法會處理所接收的所有鍵盤訊息<xref:System.Windows.Forms.Control.WndProc%2A>控制項的方法。|  
|<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>|此方法會將鍵盤訊息傳送至控制項的父代。 如果<xref:System.Windows.Forms.Control.ProcessKeyPreview%2A>會傳回`true`，不會產生按鍵事件，否則<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>呼叫。|  
|<xref:System.Windows.Forms.Control.ProcessKeyEventArgs%2A>|這個方法會引發<xref:System.Windows.Forms.Control.KeyDown>， <xref:System.Windows.Forms.Control.KeyPress>，和<xref:System.Windows.Forms.Control.KeyUp>適當的事件。|  
  
## <a name="overriding-keyboard-methods"></a>覆寫鍵盤方法  
 若已前置處理及處理鍵盤訊息，有許多方法可用於覆寫；不過，有些方法是更好的選擇 (相較於其他方法)。 下表顯示您可能想要完成的工作，以及覆寫鍵盤方法的最佳方式。 如需有關如何覆寫方法的詳細資訊，請參閱 <<c0> [ 覆寫屬性和方法在衍生類別](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md#overriding-properties-and-methods-in-derived-classes)。  
  
|工作|方法|  
|----------|------------|  
|攔截導覽鍵並引發<xref:System.Windows.Forms.Control.KeyDown>事件。 例如，您希望在文字方塊中處理 TAB 和 Return 鍵。|覆寫 <xref:System.Windows.Forms.Control.IsInputKey%2A>。 **注意：** 或者，您可以處理<xref:System.Windows.Forms.Control.PreviewKeyDown>事件和 set<xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A>的<xref:System.Windows.Forms.PreviewKeyDownEventArgs>到`true`針對您想要的索引鍵。|  
|在控制項上執行特殊輸入或導覽處理。 例如，您想使用清單控制項中的方向鍵來變更所選的項目。|覆寫 <xref:System.Windows.Forms.Control.ProcessDialogKey%2A>|  
|攔截導覽鍵並引發<xref:System.Windows.Forms.Control.KeyPress>事件。 例如，在微調方塊控制項中，您想要多次按方向鍵以加快項目的進度。|覆寫 <xref:System.Windows.Forms.Control.IsInputChar%2A>。|  
|執行特殊輸入或導覽處理期間<xref:System.Windows.Forms.Control.KeyPress>事件。 例如，在清單控制項中按住 "r" 按鍵，可略過以字母 r 開頭的項目。|覆寫 <xref:System.Windows.Forms.Control.ProcessDialogChar%2A>|  
|執行自訂助憶鍵處理；例如，您想要處理工具列內含主控描繪按鈕上的助憶鍵。|覆寫 <xref:System.Windows.Forms.Control.ProcessMnemonic%2A>。|  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.Keys>
- <xref:System.Windows.Forms.Control.WndProc%2A>
- <xref:System.Windows.Forms.Control.PreProcessMessage%2A>
- [My.Computer.Keyboard 物件](~/docs/visual-basic/language-reference/objects/my-computer-keyboard-object.md)
- [存取鍵盤](~/docs/visual-basic/developing-apps/programming/computer-resources/accessing-the-keyboard.md)
- [使用鍵盤事件](using-keyboard-events.md)
