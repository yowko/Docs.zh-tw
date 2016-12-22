---
title: "How to: Disable Adding and Deleting DataRepeater Items (Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DataRepeater, disabling delete"
  - "DataRepeater, disabling add"
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Disable Adding and Deleting DataRepeater Items (Visual Studio)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

根據預設，使用者可以在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項中加入或刪除項目。  使用者可以加入新項目的方式有二，一是在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> 獲得焦點 \(Focus\) 時按 CTRL\+N，二是在 <xref:System.Windows.Forms.BindingNavigator> 控制項上按一下 \[**AddNewItem**\] 按鈕。  使用者可以刪除項目的方式有二，一是在 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> 獲得焦點時按 DELETE，二是在 <xref:System.Windows.Forms.BindingNavigator> 控制項上按一下 \[**DeleteItem**\] 按鈕。  
  
 您可以在設計階段或執行階段，停用加入和 \(或\) 刪除功能。  
  
### 若要在設計階段停用加入和 \(或\) 刪除功能  
  
1.  在 \[Windows Form 設計工具\] 中，選取 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 控制項。  
  
    > [!NOTE]
    >  您必須選取控制項的下方區段。  如果選取項目樣板區段，將會顯示不同的屬性集 \(Property Set\)。  
  
2.  在 \[屬性\] 視窗中，將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> 屬性設定為 \[**False**\]。  
  
3.  將 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> 屬性設定為 \[**False**\]。  
  
4.  在 \[Windows Form 設計工具\] 中，選取 <xref:System.Windows.Forms.BindingNavigator> 控制項，然後按一下 \[**AddNewItem**\] 按鈕 \(有加號的按鈕\)。  
  
5.  在 \[屬性\] 視窗中，將 <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> 屬性設定為 \[**False**\]。  
  
6.  在 \[Windows Form 設計工具\] 中，選取 <xref:System.Windows.Forms.BindingNavigator> 控制項，然後按一下 \[**DeleteItem**\] 按鈕 \(有紅色 X 的按鈕\)。  
  
7.  在 \[屬性\] 視窗中，將 <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> 屬性設定為 \[**False**\]。  
  
8.  在 \[元件匣\] 中，選取 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> 繫結的 <xref:System.Windows.Forms.BindingSource>。  
  
9. 在 \[屬性\] 視窗中，將 <xref:System.Windows.Forms.BindingSource.AllowNew%2A> 屬性設定為 \[**False**\]。  
  
10. 在 \[Windows Form 設計工具\] 中，按兩下 \[**DeleteItem**\] 按鈕開啟 \[程式碼編輯器\]。  
  
11. 在 \[事件\] 下拉式清單中，選取 \[`BindingNavigatorDeleteItem_EnabledChanged`\] 事件。  
  
12. 將下列程式碼加入至 `BindingNavigatorDeleteItem_EnabledChanged` 事件處理常式：  
  
     [!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  這是一個必要步驟，因為每次目前資料錄變更時，<xref:System.Windows.Forms.BindingSource> 都會啟用 \[**DeleteItem**\] 按鈕。  
  
### 若要在執行階段停用加入和 \(或\) 刪除功能  
  
1.  在 \[Windows Form 設計工具\] 中，按兩下表單開啟 \[程式碼編輯器\]。  
  
2.  將下列程式碼加入至 \[`Form_Load`\] 事件：  
  
     [!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  將下列程式碼加入至 `BindingNavigatorDeleteItem_EnabledChanged` 事件處理常式：  
  
     [!code-cs[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  這是一個必要步驟，因為每次目前資料錄變更時，<xref:System.Windows.Forms.BindingSource> 都會啟用 \[**DeleteItem**\] 按鈕。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>   
 [Introduction to the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)   
 [Troubleshooting the DataRepeater Control](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)