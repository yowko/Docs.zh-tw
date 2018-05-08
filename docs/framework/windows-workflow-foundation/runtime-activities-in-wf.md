---
title: WF 中的執行階段活動
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: 7981d3f75c8fd2d0ddd2ae0233f425c2907c270c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="runtime-activities-in-wf"></a>WF 中的執行階段活動
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 提供幾種系統供應的活動以存取工作流程執行階段的功能，例如持續性和終止。  
  
|活動|描述|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|明確要求工作流程保存其狀態。|  
|<xref:System.Activities.Statements.TerminateWorkflow>|終止執行中的工作流程執行個體。|  
|<xref:System.Activities.Statements.NoPersistScope>|會防止任何子活動保存的容器活動。|
