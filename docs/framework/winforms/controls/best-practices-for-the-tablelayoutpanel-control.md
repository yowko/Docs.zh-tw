---
title: TableLayoutPanel 控制項的最佳作法
ms.date: 03/30/2017
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
ms.openlocfilehash: 57abf3527af146f1ce918bcabbc6a5a34bfb9b34
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011723"
---
# <a name="best-practices-for-the-tablelayoutpanel-control"></a>TableLayoutPanel 控制項的最佳作法
<xref:System.Windows.Forms.TableLayoutPanel>控制項提供功能強大的版面配置功能，您應該仔細考慮您的 Windows Forms 上使用之前。  
  
## <a name="recommendations"></a>建議  
 下列建議可協助您使用<xref:System.Windows.Forms.TableLayoutPanel>控制項其最佳的利用。  
  
### <a name="targeted-use"></a>目標的使用  
 使用<xref:System.Windows.Forms.TableLayoutPanel>謹慎控制。 您不應該使用它在所有情況下，需要可調整大小的版面配置。 下列清單描述使用的最大的版面配置<xref:System.Windows.Forms.TableLayoutPanel>控制項：  
  
- 在其中有多個部分彼此依比例調整表單的版面配置。  
  
- 要修改或動態產生在執行階段，如有增加或減少的使用者可自訂欄位的資料輸入表單的配置會根據喜好設定。  
  
- 應該保持為整體的固定大小的版面配置。 比方說，您可能會有對話方塊，應保持小於 800 x 600 解析度，但您需要支援當地語系化的字串。  
  
 下列清單將描述並不能享有大幅使用的版面配置<xref:System.Windows.Forms.TableLayoutPanel>控制項：  
  
- 簡單資料輸入表單具有單一資料行的標籤和文字輸入區域的單一資料行。  
  
- 以單一大型的表單顯示時的調整大小，就會發生應填滿所有可用的空間的區域。 這個範例是一個表單來顯示單一<xref:System.Windows.Forms.PropertyGrid>控制項。 在此情況下，使用錨定，因為重新調整表單大小時，沒有其他項目應該展開。  
  
 請謹慎選擇哪些控制項需要位於<xref:System.Windows.Forms.TableLayoutPanel>控制項。 如果您有您的文字，使用錨定的 30%的成長的空間，請考慮使用<xref:System.Windows.Forms.Control.Anchor%2A>只顯示屬性。 如果您可以評估您的版面配置所需的空間，使用<xref:System.Windows.Forms.Control.Dock%2A>並<xref:System.Windows.Forms.Control.Anchor%2A>遠比預估的剩餘空間的詳細資料和<xref:System.Windows.Forms.Control.AutoSize%2A>行為。  
  
 一般而言，當設計您的版面配置與<xref:System.Windows.Forms.TableLayoutPanel>控制項，讓設計越簡單越好。  
  
### <a name="use-the-document-outline-window"></a>使用 [文件大綱] 視窗  
 [文件大綱] 視窗可讓您的配置，您可以使用它來操作控制項的疊置順序和父子式關聯性的樹狀檢視。 從**檢視 功能表**，選取**其他 Windows**，然後選取**文件大綱**。  
  
### <a name="avoid-nesting"></a>避免巢狀結構  
 避免其他的巢狀<xref:System.Windows.Forms.TableLayoutPanel>控制項內<xref:System.Windows.Forms.TableLayoutPanel>控制項。 偵錯巢狀版面配置可能很困難。  
  
### <a name="avoid-visual-inheritance"></a>避免視覺繼承  
 <xref:System.Windows.Forms.TableLayoutPanel>控制項不支援在 Windows Form 設計工具的視覺化繼承。 A <xref:System.Windows.Forms.TableLayoutPanel> 「 已鎖定 」 在設計階段，會出現在衍生類別中的控制項。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
