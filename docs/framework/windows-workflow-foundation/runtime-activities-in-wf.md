---
title: "WF 中的執行階段活動"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3386138f01d4865b02ca821a30da68e5d73b64e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-activities-in-wf"></a>WF 中的執行階段活動
[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] 提供幾種系統供應的活動以存取工作流程執行階段的功能，例如持續性和終止。  
  
|活動|描述|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|明確要求工作流程保存其狀態。|  
|<xref:System.Activities.Statements.TerminateWorkflow>|終止執行中的工作流程執行個體。|  
|<xref:System.Activities.Statements.NoPersistScope>|會防止任何子活動保存的容器活動。|
