---
title: "工具箱服務 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 742212d0-445e-41ed-9739-9ee848ce7f1b
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 工具箱服務
這個範例示範如何根據工作流程的內容來更新 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 工具箱活動。此範例包含會隨著自訂活動是否選取而變更工具箱內容的工作流程。  
  
## 討論  
 在工作流程撰寫期間，客戶通常希望工具箱是與內容相關的。例如，使用者可能想要確認當特定活動加入至工作流程時，工具箱會顯示一些其他活動。如果從工作流程移除活動，工具箱應該根據網域需求適當回應。  
  
 在重新裝載的工作流程設計工具中，您可以控制工具箱控制項，並確認主機會根據工作流程中的模型變更來觸發工具箱控制項中的適當變更。不過，在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中，工具箱不是由使用者控制，因此需要介面修改其內容。`IActivityToolboxService` 就是該介面。  
  
 API 提供下列四個方法。  
  
```  
public interface IActivityToolboxService   
{   
        void AddCategory(string categoryName);   
        void RemoveCategory(string categoryName);   
        void AddItem(string qualifiedTypeName, string categoryName);   
        void RemoveItem(string qualifiedTypeName, string categoryName);   
        IList<string> EnumCategories();   
        IList<string> EnumItems(string categoryName);   
}  
```  
  
#### 若要安裝、建立及執行範例  
  
1.  使用 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 開啟 WorkflowSimulator.sln 方案檔案。  
  
2.  按 CTRL\+SHIFT\+B 建置此方案。  
  
3.  開啟 Workflow.xaml 檔案。  
  
4.  從工具箱拖放 \[**CustomActivity**\]，加入此項目。請注意，額外的工具箱類別目錄名稱為：\[**新增 WF 類別目錄**\]，其具有額外的活動 **Assign**。  
  
5.  現在將另一個活動拖曳至其中，取消選取 \[**CustomActivity**\]。  
  
6.  工具箱底下，\[**新增 WF 類別目錄**\] 類別目錄中的 \[**Assign**\] 項目現在已移除。此外，因為類別目錄中沒有其他項目，類別目錄也會移除。  
  
7.  再次選取 \[**CustomActivity**\]，類別目錄和 **Assign** 活動就會重新加入。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Designer\IActivityToolboxService`