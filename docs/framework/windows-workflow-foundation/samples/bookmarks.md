---
title: Bookmarks2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 035fadb2-49fa-4ac7-b398-daf138f66e87
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d3a1e0a966fcd5d89cc30456b46a11ae7d54731e
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/28/2017
---
# <a name="bookmarks"></a>書籤
這個範例示範如何撰寫自訂活動，建立可接收外部輸入的書籤。 範例中還包括在工作流程中使用自訂活動的基本主控台應用程式，並且示範如何探索和繼續與執行中工作流程執行個體相關聯的書籤。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]書籤，請參閱[書籤](../../../../docs/framework/windows-workflow-foundation/bookmarks.md)。  
  
### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 [Bookmarks.sln] 範例方案。  
  
2.  若要建置此方案，請按 CTRL+SHIFT+B。  
  
3.  若要執行範例，請按 CTRLl + F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CodeBodied\Bookmarks`