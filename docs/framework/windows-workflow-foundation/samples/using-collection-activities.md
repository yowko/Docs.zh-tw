---
title: "使用集合活動 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e1977cf8-1695-4071-b946-7046fe39601e
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# 使用集合活動
這個範例會示範如何透過實作 <xref:System.Collections.ICollection> 介面的類別使用集合活動 \(<xref:System.Activities.Statements.AddToCollection%601>、<xref:System.Activities.Statements.ClearCollection%601>、<xref:System.Activities.Statements.ExistsInCollection%601> 和 <xref:System.Activities.Statements.RemoveFromCollection%601>\)，以及如何建立自訂活動，以便逐一查看集合以列印集合中每一個項目的內容。名為 `PrintCollection` 的自訂活動會將名為 `Numbers` 之集合的項目成員列印到主控台。  
  
 下表描述四個活動，這些活動會提供工作流程的集合操作。  
  
|活動名稱|說明|  
|----------|--------|  
|<xref:System.Activities.Statements.AddToCollection%601>|將項目加入至集合。|  
|<xref:System.Activities.Statements.ClearCollection%601>|清除集合中的所有項目|  
|<xref:System.Activities.Statements.ExistsInCollection%601>|如果指定的項目存在於集合中，則傳回 `true`。|  
|<xref:System.Activities.Statements.RemoveFromCollection%601>|從集合中移除項目。|  
  
 此範例是由兩個方案所組成，一個位於 CodedWorkflow 目錄底下，另一個位於 DesignerWorkflow 目錄底下。這兩個方案會示範針對相同的用途使用活動的兩個不同方式。  
  
||||  
|-|-|-|  
|方案|說明|主要檔案|  
|CodedWorkflow|範例用戶端應用程式，可示範如何以程式設計方式叫用集合活動。|**PrintCollection.cs**：可將集合中的每一個項目列印到主控台的協助程式活動。<br /><br /> **Program.cs**：以程式設計方式建置包含一系列集合活動的序列活動，然後執行此活動。|  
|DesignerWorkflow|範例用戶端應用程式，可示範如何以宣告方式在工作流程設計工具中使用集合活動。|**CollectionWorkflow.xaml**：以宣告方式透過使用集合活動的設計工具所建立的工作流程。<br /><br /> **PrintCollection.cs**：可將集合中的每一個項目列印到主控台的協助程式活動。<br /><br /> **Program.cs**：叫用 CollectionWorkflow.xaml 中所描述的工作流程。|  
  
 在示範中，將會使用稱為 `PrintCollection` 的自訂活動，將 `Numbers` 集合的項目成員列印到主控台。  
  
#### 若要使用這個範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 Collection.sln 方案檔案。  
  
2.  若要建置此方案，請按下 CTRL\+SHIFT\+B。  
  
3.  若要執行此方案，請按下 CTRL\+F5。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Collection`  
  
## 請參閱