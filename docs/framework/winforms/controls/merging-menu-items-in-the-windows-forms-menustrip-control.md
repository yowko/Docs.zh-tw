---
title: 合併 Windows Form MenuStrip 控制項中的功能表項目
ms.date: 03/30/2017
helpviewer_keywords:
- MenuStrip [Windows Forms], merging
- merging [Windows Forms], general concepts
ms.assetid: 95e113ba-f362-4dda-8a76-6d95ddc45cee
ms.openlocfilehash: 2782ae483d673f8f1eccab10876aca858737260a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539785"
---
# <a name="merging-menu-items-in-the-windows-forms-menustrip-control"></a>合併 Windows Form MenuStrip 控制項中的功能表項目
如果您有多個文件介面 (MDI) 應用程式，您可以合併到父表單的功能表的功能表項目或從子表單的整個功能表。  
  
 本主題說明與合併的 MDI 應用程式中的功能表項目相關聯的基本概念。  
  
## <a name="general-concepts"></a>一般概念  
 合併程序牽涉到的目標，而且原始檔控制：  
  
-   目標是<xref:System.Windows.Forms.MenuStrip>main 或 MDI 父表單的項目，其中您要合併的功能表項目控制項。  
  
-   來源是<xref:System.Windows.Forms.MenuStrip>MDI 子表單，其中包含您想要合併到目標 功能表的功能表項目上的控制項。  
  
 <xref:System.Windows.Forms.MenuStrip.MdiWindowListItem%2A>屬性會識別將會填入目前的 MDI 標題的下拉式清單中父表單的 MDI 子視窗的功能表項目。 比方說，您通常會列出在目前開啟的 MDI 子系**視窗**功能表。  
  
 <xref:System.Windows.Forms.ToolStripMenuItem.IsMdiWindowListEntry%2A>屬性會識別功能表項目來自<xref:System.Windows.Forms.MenuStrip>的 MDI 子表單上。  
  
 您可以在手動或自動合併功能表項目。 這兩種方法中，相同的方式合併的功能表項目，但會以不同的方式，本主題稍後的 「 手動合併 」 和 「 自動合併 」 章節所討論啟動合併。 在手動和自動合併，每個合併動作會影響下一步合併動作。  
  
 <xref:System.Windows.Forms.MenuStrip> 合併移動功能表項目從某個<xref:System.Windows.Forms.ToolStrip>之間而非複製，因為已使用的情況下<xref:System.Windows.Forms.MainMenu>。  
  
## <a name="mergeaction-values"></a>MergeAction 值  
 您在來源中的功能表項目上設定合併動作<xref:System.Windows.Forms.MenuStrip>使用<xref:System.Windows.Forms.MergeAction>屬性。  
  
 下表描述的意義和一般使用可用的合併動作。  
  
|MergeAction 值|描述|一般用法|  
|-----------------------|-----------------|-----------------|  
|<xref:System.Windows.Forms.MergeAction.Append>|（預設值）將來源項目加入至目標項目集合的結尾。|功能表項目加入功能表的結束時啟動程式的某些部分。|  
|<xref:System.Windows.Forms.MergeAction.Insert>|將來源項目加入至目標項目的集合，在所指定的位置<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>來源項目上設定的屬性。|啟動程式的某些部分時，請至中間或功能表的開頭加入功能表項目。<br /><br /> 如果值<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>相同的兩個功能表項目，就會加入以反向順序。 設定<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>適當地保留原始的順序。|  
|<xref:System.Windows.Forms.MergeAction.Replace>|尋找文字的相符項目，或使用<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>值，如果沒有文字相符項目發現，然後將相符的目標功能表項目取代來源功能表項目。|取代來源功能表項目沒有其他同名的目標功能表項目。|  
|<xref:System.Windows.Forms.MergeAction.MatchOnly>|尋找文字的相符項目，或使用<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>如果沒有文字相符項目找到，並將所有下拉式項目從來源到目標值。|建立功能表結構插入或將功能表項目新增到子功能表，或移除子功能表的功能表項目。 例如，您可以加入功能表項目從 MDI 子系主要<xref:System.Windows.Forms.MenuStrip>**存**功能表。<br /><br /> <xref:System.Windows.Forms.MergeAction.MatchOnly> 可讓您瀏覽功能表結構而不採取任何動作。 它提供方法來評估後續項目。|  
|<xref:System.Windows.Forms.MergeAction.Remove>|尋找文字的相符項目，或使用<xref:System.Windows.Forms.ToolStripItem.MergeIndex%2A>值，如果沒有文字相符項目發現，然後在目標中移除的項目。|從目標中移除功能表項目<xref:System.Windows.Forms.MenuStrip>。|  
  
## <a name="manual-merging"></a>手動合併  
 只有<xref:System.Windows.Forms.MenuStrip>控制項參與自動合併。 若要結合的其他控制項項目，例如<xref:System.Windows.Forms.ToolStrip>和<xref:System.Windows.Forms.StatusStrip>控制項，您必須將其合併以手動方式，藉由呼叫<xref:System.Windows.Forms.ToolStripManager.Merge%2A>和<xref:System.Windows.Forms.ToolStripManager.RevertMerge%2A>您所需的程式碼中的方法。  
  
## <a name="automatic-merging"></a>自動合併  
 您可以使用藉由啟用來源表單為 MDI 應用程式自動合併。 若要使用<xref:System.Windows.Forms.MenuStrip>MDI 應用程式中，設定<xref:System.Windows.Forms.Form.MainMenuStrip%2A>屬性目標<xref:System.Windows.Forms.MenuStrip>使來源上執行的合併動作<xref:System.Windows.Forms.MenuStrip>會反映在目標<xref:System.Windows.Forms.MenuStrip>。  
  
 您可以觸發自動合併藉由啟用<xref:System.Windows.Forms.MenuStrip>MDI 來源。 在啟動過程中，來源<xref:System.Windows.Forms.MenuStrip>合併到 MDI 目標。 當新的表單變成作用中時，合併會還原上一個表單，而且觸發新的表單上。 您可以設定來控制此行為<xref:System.Windows.Forms.ToolStripItem.MergeAction%2A>屬性視需要在每個<xref:System.Windows.Forms.ToolStripItem>，以及設定<xref:System.Windows.Forms.ToolStrip.AllowMerge%2A>上每個屬性<xref:System.Windows.Forms.MenuStrip>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolStripManager>  
 <xref:System.Windows.Forms.MenuStrip>  
 [MenuStrip 控制項](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [操作說明：使用 MenuStrip 建立 MDI 視窗清單](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md)  
 [操作說明：設定 MDI 應用程式的自動功能表合併功能](../../../../docs/framework/winforms/controls/how-to-set-up-automatic-menu-merging-for-mdi-applications.md)
