---
title: "工作 1：建立新的 Windows Presentation Foundation 應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# 工作 1：建立新的 Windows Presentation Foundation 應用程式
在這個工作中，您將會使用 WPF 應用程式 Visual Studio 範本建立一個空的 [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] 應用程式，再將參考加入至適當的 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 工作流程組件。  
  
### 若要建立 WPF 應用程式專案  
  
1.  開啟 [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] 並在 \[**檔案**\] 功能表上指向 \[**新增**\]，然後按一下 \[**專案**\]。  
  
2.  在 \[**新增專案**\] 對話方塊中，從方塊左邊的 \[**已安裝的範本**\] 窗格中選取 \[**Visual C\#**\] 或 \[**Visual Basic**\]。如果沒有出現您所選的語言，請查看 \[**其他語言**\]。  
  
3.  選取 \[**已安裝的範本**\] 窗格中的 \[**Windows**\]。  
  
4.  在上方窗格中，確認已選取下拉式清單方塊中的 \(預設值\) \[**.NET Framework 4**\]，然後選取 \[**WPF 應用程式**\]。  
  
5.  在視窗底部將專案名稱設定為 **HostingApplication**。  
  
6.  將方案名稱設定為 **RehostingTheDesigner**。  
  
7.  按一下 \[**確定**\] 建立應用程式專案。[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] 會為應用程式建立基本 WPF UI，並且包含合適的 XAML 和程式碼後置檔案。  
  
8.  將參考加入至 **WorkflowModel** 組件。若要執行這項操作，請在 \[**方案總管**\] 中以滑鼠右鍵按一下 \[**HostingApplication**\] 專案，並且選取 \[**加入參考**\]。  
  
9. 在 \[**加入參考**\] 對話方塊中按一下 \[**.NET**\] 索引標籤，按住 CTRL 鍵，選取下列組件，然後按一下 \[**確定**\]：  
  
    -   System.Activities  
  
    -   System.Activities.Presentation  
  
    -   System.Activities.Core.Presentation  
  
10. 按一下 \[**確定**\]。  
  
11. 若要了解如何裝載工作流程設計工具設計畫布，請參閱[工作 2：裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation//task-2-host-the-workflow-designer.md)。  
  
## 請參閱  
 [重新裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation//rehosting-the-workflow-designer.md)   
 [工作 2：裝載工作流程設計工具](../../../docs/framework/windows-workflow-foundation//task-2-host-the-workflow-designer.md)