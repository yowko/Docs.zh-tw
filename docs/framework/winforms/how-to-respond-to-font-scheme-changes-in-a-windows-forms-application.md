---
title: 如何：回應 Windows Forms 應用程式中的字型配置變更
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: 455609ea602f450803718f5be34618b087560d21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539448"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>如何：回應 Windows Forms 應用程式中的字型配置變更
在 Windows 作業系統中，使用者可以變更全系統字型設定，讓預設字型看起來更大或變小。 變更這些字型設定是重要的是視覺障礙者，並且需要讀取他們的螢幕上文字的較大類型的使用者。 您可以調整 Windows Form 應用程式由增加或減少大小的表單和內含之所有文字的字型配置變更時回應這些變更。 如果您想要以動態方式容納變更字型大小表單時，您可以將程式碼加入至表單。  
  
 一般而言，Windows Forms 所使用的預設字型是所傳回的字型<xref:Microsoft.Win32>命名空間呼叫`GetStockObject(DEFAULT_GUI_FONT)`。 這個呼叫所傳回的字型僅會變更螢幕解析度變更時。 下列程序所示，您的程式碼必須變更預設字型<xref:System.Drawing.SystemFonts.IconTitleFont%2A>來回應以字型大小的變更。  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>使用桌面的字型和回應的字型配置變更  
  
1.  建立您的表單，並加入您想要的控制項。 如需詳細資訊，請參閱[How to： 從命令列建立 Windows Forms 應用程式](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md)和[Windows Form 上使用的控制項](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)。  
  
2.  將參考加入<xref:Microsoft.Win32>您的程式碼的命名空間。  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  將下列程式碼加入至表單連結所需的事件處理常式，並變更表單的使用中的預設字型的建構函式。  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  實作的處理常式<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>事件，讓自動縮放表單時<xref:Microsoft.Win32.UserPreferenceCategory.Window>類別目錄的變更。  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  最後，實作的處理常式<xref:System.Windows.Forms.Form.FormClosing>中斷連結的事件<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>事件處理常式。  
  
> [!IMPORTANT]
>  包括此程式碼的失敗會導致您的應用程式會造成記憶體流失。  
  
 [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
 [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
1.  編譯並執行程式碼。  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>若要手動變更在 Windows XP 中的字型配置  
  
1.  當 Windows Forms 應用程式正在執行時，以滑鼠右鍵按一下 Windows 桌面上，然後選擇 **屬性**從捷徑功能表。  
  
2.  在**顯示屬性**對話方塊中，按一下 [**外觀**] 索引標籤。  
  
3.  從**字型大小**下拉式清單方塊中，選取新字型的大小。  
  
     您會發現表單回應執行階段變更桌面的字型配置中。 當使用者變更之間**一般**，**大字型**，和**超大型字**，變更字型的表單，並正確地進行縮放。  
  
## <a name="example"></a>範例  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 在此程式碼範例 constructer 包含呼叫`InitializeComponent`，也就是當您在 Visual Studio 中建立新的 Windows Form 專案時定義。 如果您要建置命令列上的應用程式，請移除這行程式碼。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 [Windows Forms 中的自動縮放比例](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)
