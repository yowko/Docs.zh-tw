---
title: "如何：設計可適當回應當地語系化的 Windows Form 配置 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "應用程式設計, 當地語系化"
  - "當地語系化, Windows Forms 配置"
  - "TableLayoutPanel 控制項 [Windows Form]"
  - "Windows Form, 當地語系化"
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 如何：設計可適當回應當地語系化的 Windows Form 配置
建立準備好當地語系化的表單，將會大幅加速開發國際市場。  您可以使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來實作版面配置，當控制項因 <xref:System.Windows.Forms.Control.Text%2A> 屬性值變更而調整大小時，它會依正常程序回應。  
  
## 範例  
 在您翻譯顯示字串值為其他語言時，此表單會示範如何建立可按比例調整的版面配置。  這個翻譯的過程稱為*「當地語系化」*\(localization\)。  如需詳細資訊，請參閱[當地語系化](../../../../docs/standard/globalization-localization/localization.md)。  
  
 在 Visual Studio 中對於本工作有更詳盡的支援。  另請參閱[逐步解說：建立可調整比例以配合當地語系化的配置](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\))。  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  [如何：在 TableLayoutPanel 控制項中對齊和縮放控制項](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))  
  
2.  [逐步解說：使用 FlowLayoutPanel 來排列 Windows Form 上的控制項](http://msdn.microsoft.com/library/z9w7ek2f%20\(v=vs.110\))  
  
3.  [如何：擴展 TableLayoutPanel 控制項中的資料列和資料行](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))  
  
4.  [如何：編輯 TableLayoutPanel 控制項中的資料行和資料列](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))  
  
5.  [逐步解說：使用 Windows Form 控制項中的智慧標籤執行一般工作](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))  
  
6.  [逐步解說：使用 TableLayoutPanel 排列 Windows Form 上的控制項](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
7.  [逐步解說：使用邊框距離、邊界和 AutoSize 屬性來配置 Windows Form 控制項](http://msdn.microsoft.com/library/3z3f9e8b%20\(v=vs.110\))  
  
8.  [如何‎：使用 AutoSize 和 TableLayoutPanel 控制項支援 Windows Form 的當地語系化](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))  
  
9. [逐步解說： 建立可調整大小的 Windows Form 用於資料輸入](http://msdn.microsoft.com/library/991eahec%20\(v=vs.110\))  
  
## 編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 如需從 [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] 或 [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] 的命令列建置這個範例的相關資訊，請參閱[從命令列建置](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) 或[使用 csc.exe 建置命令列](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。  您也可以透過將程式碼貼入新的專案，在 [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] 中建置這個範例。  另請參閱[如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228%20\(v=vs.110\))。  
  
## 請參閱  
 <xref:System.Windows.Forms.TableLayoutPanel>   
 <xref:System.Windows.Forms.FlowLayoutPanel>   
 [當地語系化](../../../../docs/standard/globalization-localization/localization.md)