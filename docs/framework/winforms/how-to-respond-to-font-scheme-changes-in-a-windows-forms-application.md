---
title: "如何：回應 Windows Form 應用程式中的字型配置變更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Windows Form, 字型配置變更"
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 如何：回應 Windows Form 應用程式中的字型配置變更
在 Windows 作業系統中，使用者可以變更整個系統的字型設定，讓預設字型看起來大一點或小一點。  對於視障使用者或者需要大型字才能閱讀螢幕上文字的使用者而言，變更這些字型設定是一件很重要的事。  每當字型配置變更時，您可以增加或減小表單和所有內含文字的大小，藉此調整 Windows Form 應用程式，以反應這些變更。  如果您想要讓表單以動態方式反應字型大小的變更，可以在表單中加入程式碼。  
  
 一般而言，Windows Form 使用的預設字型是由 `GetStockObject(DEFAULT_GUI_FONT)` 的 <xref:Microsoft.Win32> 命名空間呼叫所傳回的字型。  只有當螢幕解析度變更時，這個呼叫所傳回的字型才會變更。  如下列程序所示，程式碼必須將預設字型變更為 <xref:System.Drawing.SystemFonts.IconTitleFont%2A> 以回應字型大小的變更。  
  
### 若要使用桌面字型並回應字型配置變更  
  
1.  建立表單，然後將您要的控制項加入至表單。  如需詳細資訊，請參閱 [如何：從命令列建立 Windows Form 應用程式](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md)和 [在 Windows Form 上使用的控制項](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)。  
  
2.  在程式碼中加入 <xref:Microsoft.Win32> 命名空間的參考。  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  將下列程式碼加入至表單的建構函式中，以連結所需的事件處理常式，並變更表單所用的預設字型。  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  實作 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> 事件的處理常式，這會讓表單在 <xref:Microsoft.Win32.UserPreferenceCategory> 分類變更時自動調整大小。  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  最後，請實作 <xref:System.Windows.Forms.Form.FormClosing> 事件的處理常式，這會中斷 <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> 事件處理常式的連結。  
  
> [!IMPORTANT]
>  若沒有加入這個程式碼，應用程式會發生記憶體遺漏現象。  
  
 [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
 [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
1.  編譯並執行程式碼。  
  
### 若要手動變更 Windows XP 的字型配置  
  
1.  當 Windows Form 應用程式正在執行的時候，在 Windows 桌面上按一下滑鼠右鍵，然後從捷徑功能表中選取 \[**內容**\]。  
  
2.  在 \[**顯示內容**\] 對話方塊中，按一下 \[**外觀**\] 索引標籤。  
  
3.  從 \[**字型大小**\] 下拉式清單方塊中，選取另一個字型大小。  
  
     您會注意到現在表單會反應桌面上字型配置在執行階段的變更。  當使用者在 \[**標準**\]、\[**大型字**\] 和 \[**超大型字**\] 之間變換設定時，表單會變更字型並正確地進行縮放。  
  
## 範例  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 這個程式碼範例中的建構函式包含了對 `InitializeComponent` 的呼叫，這是在 Visual Studio 中建立新的 Windows Form 專案時所定義的。  如果您是在命令列中建置應用程式，請移除這一行程式碼。  
  
## 請參閱  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>   
 [Windows Form 中的自動縮放比例](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)