---
title: 使用活動類別撰寫工作流程活動
ms.date: 03/30/2017
ms.assetid: 7b7b1c66-f093-43c3-b4d1-7173b46516da
ms.openlocfilehash: abdabc46aa54e19d5a04c5b34d6d2b9be07488d6
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57711859"
---
# <a name="workflow-activity-authoring-using-the-activity-class"></a>使用活動類別撰寫工作流程活動
最基本的方式，來建立使用 Windows Workflow Foundation (WF) 中的活動[!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]是建立繼承自類別<xref:System.Activities.Activity>建立功能的組合自訂活動或活動從[內建活動程式庫](net-framework-4-5-built-in-activity-library.md)。 本主題示範如何建立會寫入兩個訊息至主控台的活動。

### <a name="to-create-a-custom-activity-using-the-activity-designer"></a>若要使用活動設計工具建立自訂活動

1.  開啟 Visual Studio 2012。

2.  依序選取 [檔案]、[新增]、[專案]。 選取  **Workflow 4.0**下方**Visual C#** 中**專案類型**視窗中，然後選取**v2010**節點。 選取 **活動程式庫**中**範本**視窗。 將新專案命名為 HelloActivity。

3.  開啟新活動。  將 <xref:System.Activities.Statements.Sequence> 活動從工具箱拖曳至設計工具介面上。

4.  將 <xref:System.Activities.Statements.WriteLine> 活動拖曳至 <xref:System.Activities.Statements.Sequence> 活動中。 請輸入`"Hello World"`（含引號） 到**文字**欄位。

5.  將第二個 <xref:System.Activities.Statements.WriteLine> 活動拖曳至 <xref:System.Activities.Statements.Sequence> 活動，放在第一個活動下方。 請輸入`"Goodbye"`（含引號） 到**文字**欄位。
