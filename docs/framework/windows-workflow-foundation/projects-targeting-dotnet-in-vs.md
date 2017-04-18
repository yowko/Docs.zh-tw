---
title: "針對 Visual Studio 2010 中的 .NET Framework 3.0 及 3.5 撰寫專案 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 針對 Visual Studio 2010 中的 .NET Framework 3.0 及 3.5 撰寫專案
您可以使用 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] 來建立以 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 3.0 或 3.5 版為目標的專案。本主題描述如何執行這個工作。  
  
> [!NOTE]
>  當加入活動時，請務必設定所需的 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 版本。在加入活動之後變更工作流程的目標版本將會導致工作流程驗證失敗。  
  
> [!WARNING]
>  在 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] 中開啟擁有 .Net Framework 3.5 活動的現有工作流程將會導致 `this.SetValue()` 發生錯誤。為了開啟之前使用舊版 .Net Framework 所建立的專案，請先在設計工具中開啟空白工作流程，然後加入 .Net Framework 3.5 活動。  
  
## 若要使用 Visual Studio 2010 建立 .NET Framework 3.0 或 3.5 專案  
  
1.  開啟 [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]。  
  
2.  依序選取 \[**檔案**\]、\[**新增**\]、\[**專案**\]。  
  
3.  在對話方塊上方的下拉式清單中，選取所需的 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 版本。  
  
## 若要升級 .NET Framework 的目標版本  
  
1.  以滑鼠右鍵按一下 \[方案總管\] 中的專案，然後選取 \[**屬性**\]。  
  
2.  在 \[**目標 Framework**\] 下拉式清單中，選取所需的版本。