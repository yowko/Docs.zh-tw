---
title: 如何：設計可適當回應當地語系化的 Windows Form 配置
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7f35a61c4ef8bbda544e36939fe4986a1017fe31
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>如何：設計可適當回應當地語系化的 Windows Form 配置
建立準備好當地語系化的表單，將會大幅加速開發國際市場。 您可以使用 <xref:System.Windows.Forms.TableLayoutPanel> 控制項來實作版面配置，當控制項因 <xref:System.Windows.Forms.Control.Text%2A> 屬性值變更而調整大小時，它會依正常程序回應。  
  
## <a name="example"></a>範例  
 在您翻譯顯示字串值為其他語言時，此表單會示範如何建立可按比例調整的版面配置。 這個翻譯的過程稱為「當地語系化」(localization)。 如需詳細資訊，請參閱[當地語系化](../../../../docs/standard/globalization-localization/localization.md)。  
  
 在 Visual Studio 中對於本工作有更詳盡的支援。  另請參閱[逐步解說：建立可調整比例以配合當地語系化的配置](http://msdn.microsoft.com/library/7k9fa71y\(v=vs.110\))。  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
1.  [操作說明：在 TableLayoutPanel 控制項中對齊和縮放控制項](http://msdn.microsoft.com/library/ms171688\(v=vs.110\))  
  
2.  [逐步解說：使用 FlowLayoutPanel 排列 Windows Forms上的控制項](http://msdn.microsoft.com/library/z9w7ek2f\(v=vs.110\))  
  
3.  [如何：擴展 TableLayoutPanel 控制項中的資料列和資料行](http://msdn.microsoft.com/library/ms171687\(v=vs.110\))  
  
4.  [如何：編輯 TableLayoutPanel 控制項中的資料行和資料列](http://msdn.microsoft.com/library/ms171686\(v=vs.110\))  
  
5.  [逐步解說：使用 Windows Forms 控制項中的智慧標籤執行一般工作](http://msdn.microsoft.com/library/xhz359sc\(v=vs.110\))  
  
6.  [逐步解說：使用 TableLayoutPanel 排列 Windows Forms 上的控制項](http://msdn.microsoft.com/library/w4yc3e8c\(v=vs.110\))  
  
7.  [逐步解說：使用邊框距離、邊界和 AutoSize 屬性配置 Windows Forms 控制項](http://msdn.microsoft.com/library/3z3f9e8b\(v=vs.110\))  
  
8.  [如何‎：使用 AutoSize 和 TableLayoutPanel 控制項支援 Windows Forms 的當地語系化](http://msdn.microsoft.com/library/1zkt8b33\(v=vs.110\))  
  
9. [逐步解說：建立適用於資料輸入且可調整大小的 Windows Form](http://msdn.microsoft.com/library/991eahec\(v=vs.110\))  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 這個範例需要：  
  
-   System、System.Data、System.Drawing 和 System.Windows.Forms 組件的參考。  
  
 Visual Basic 或 Visual C# 中建置這個範例，從命令列的相關資訊，請參閱[從命令列建置](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)或[使用 csc.exe 建置](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)。 您也可以將程式碼貼入新的專案，以建置 Visual Studio 中的這個範例。  另請參閱 [如何：使用 Visual Studio 編譯及執行完整的 Windows Form 程式碼範例](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 [當地語系化](../../../../docs/standard/globalization-localization/localization.md)
