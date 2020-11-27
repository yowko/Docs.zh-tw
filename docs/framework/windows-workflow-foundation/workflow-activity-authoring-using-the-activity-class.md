---
title: 使用活動類別撰寫工作流程活動
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: 21f1c8b1249d41029fa7a19360e96ad866c823a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293841"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>使用活動類別撰寫工作流程活動

使用 Windows Workflow Foundation (WF) 建立活動的最基本方式， [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] 就是建立一個繼承自的類別，該類別會從 <xref:System.Activities.Activity> [內建活動程式庫](net-framework-4-5-built-in-activity-library.md)組合自訂活動或活動，以建立功能。 本主題示範如何建立會寫入兩個訊息至主控台的活動。

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>若要使用活動設計工具建立自訂活動

1. 開啟 Visual Studio 2012。

2. 依序選取 [檔案]、[新增]、[專案]。 在 [**專案類型**] 視窗中選取 [ **Visual c #** ] 底下的 **工作流程 4.0** ，然後選取 [ **v2010]** ] 節點。 選取 [**範本**] 視窗中的 [**活動程式庫**]。 將新專案命名為 HelloActivity。

3. 開啟新活動。  將 <xref:System.Activities.Statements.Sequence> 活動從工具箱拖曳至設計工具介面上。

4. 將 <xref:System.Activities.Statements.WriteLine> 活動拖曳至 <xref:System.Activities.Statements.Sequence> 活動中。 `"Hello World"`在 [**文字**] 欄位中輸入具有引號的 () 。

5. 將第二個 <xref:System.Activities.Statements.WriteLine> 活動拖曳至 <xref:System.Activities.Statements.Sequence> 活動，放在第一個活動下方。 `"Goodbye"`在 [**文字**] 欄位中輸入具有引號的 () 。
