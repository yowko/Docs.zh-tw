---
title: "TableLayoutPanel 控制項的最佳作法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layout [Windows Forms]
- TableLayoutPanel control [Windows Forms], best practices
- forms [Windows Forms], best practices
- AutoSize property [Windows Forms], tableLayoutPanel control
- controls [Windows Forms], sizing
- TableLayoutPanel control [Windows Forms], AutoSize behavior
- layout [Windows Forms], AutoSize
- layout [Windows Forms], best practices
- best practices [Windows Forms], tableLayoutPanel control
- sizing [Windows Forms], automatic
- automatic sizing
ms.assetid: b6706efb-d7a4-45ec-8cf4-08fa993e3afb
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 802cc501b695f6c5cfe990bf72a4d9d2af68ba2b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a>TableLayoutPanel 控制項的最佳作法
<xref:System.Windows.Forms.TableLayoutPanel>控制項提供功能強大的配置功能，您應該先在 Windows Form 上使用仔細考慮。  
  
## <a name="recommendations"></a>建議  
 下列建議將協助您使用<xref:System.Windows.Forms.TableLayoutPanel>控制項的最佳優勢。  
  
### <a name="targeted-use"></a>目標的使用  
 使用<xref:System.Windows.Forms.TableLayoutPanel>謹慎控制。 您不應該使用所有的情況下，需要可調整大小的配置。 下列清單描述獲益最多使用的版面配置<xref:System.Windows.Forms.TableLayoutPanel>控制項：  
  
-   有多個部分彼此依比例調整表單的配置。  
  
-   要修改或動態產生在執行階段，例如有加上或扣除的使用者可自訂欄位的資料輸入表單的配置會根據喜好設定。  
  
-   應該保持為整體的固定大小的配置。 例如，您可能應保持小於 800 x 600，對話方塊中，但是您需要支援當地語系化的字串。  
  
 下列清單描述不使用大大受益的版面配置<xref:System.Windows.Forms.TableLayoutPanel>控制項：  
  
-   簡單資料項目表單的單一資料行的標籤和單一資料行的文字輸入區域。  
  
-   以單一大型的表單顯示時調整大小，就會發生應該填滿所有可用空間的區域。 舉例來說，這是一個表單來顯示單一<xref:System.Windows.Forms.PropertyGrid>控制項。 在此情況下，使用錨點，因為重新調整表單大小時，都應該展開。  
  
 請小心選擇哪些控制項需要位於<xref:System.Windows.Forms.TableLayoutPanel>控制項。 如果您有文字，以擴大使用錨定的 30%的空間，請考慮使用<xref:System.Windows.Forms.Control.Anchor%2A>只屬性。 如果您可以評估您的配置所需的空間，使用<xref:System.Windows.Forms.Control.Dock%2A>和<xref:System.Windows.Forms.Control.Anchor%2A>比預估的剩餘空間的詳細資料更容易及<xref:System.Windows.Forms.Control.AutoSize%2A>行為。  
  
 一般而言，當設計具有配置<xref:System.Windows.Forms.TableLayoutPanel>控制項，讓設計越簡單越好。  
  
### <a name="use-the-document-outline-window"></a>使用文件大綱 視窗  
 [文件大綱] 視窗可讓您的配置，您可以使用來操作控制項的疊置順序與父子式關聯性的樹狀檢視。 從**檢視 功能表**，選取**其他視窗**，然後選取**文件大綱**。  
  
### <a name="avoid-nesting"></a>避免巢狀結構  
 避免其他的巢狀<xref:System.Windows.Forms.TableLayoutPanel>內控制<xref:System.Windows.Forms.TableLayoutPanel>控制項。 偵錯巢狀的配置可能相當困難。  
  
### <a name="avoid-visual-inheritance"></a>避免視覺化繼承  
 <xref:System.Windows.Forms.TableLayoutPanel>控制項不支援在 Windows Form 設計工具的視覺化繼承。 A <xref:System.Windows.Forms.TableLayoutPanel> 「 已鎖定 」 在設計階段，會出現在衍生類別中的控制項。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>
