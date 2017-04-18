---
title: "HOW TO：在 Visual Studio 中建立 LINQ to DataSet 專案 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：在 Visual Studio 中建立 LINQ to DataSet 專案
不同的 [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] 專案類型需要特定匯入的命名空間 \(Namespace\) \(Visual Basic\) 或 `using` 指示詞 \(C\#\) 和參考。  最小需求是 System.Core.dll 的參考和 <xref:System.Linq> 的 `using` 指示詞。  根據預設，如果您建立新的 [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] 專案，系統就會提供這些項目。  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 也需要 System.Data.dll 和 System.Data.DataSetExtensions.dll 的參考以及 `Imports` \(Visual Basic\) 或 `using` \(C\#\) 指示詞。  
  
 如果您要從舊版 Visual Studio 升級專案，可能必須手動提供這些 LINQ 相關的參考。  此外，您可能也必須手動將專案設定為以 .NET Framework 3.5 版為目標。  
  
> [!NOTE]
>  如果您要從命令提示字元建立，就必須手動參考 `drive`**:**\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.5 中的 LINQ 相關 DLL。  
  
### 以 .NET Framework 3.5 為目標  
  
1.  在 [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] 中，建立新的 Visual Basic 或 C\# 專案。或者，您也可以開啟在 Visual Studio 2005 中建立的 Visual Basic 或 C\# 專案，然後遵循提示，將它轉換成 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 專案。  
  
2.  若為 C\# 專案，請按一下 \[**專案**\] 功能表，然後按一下 \[**屬性**\]。  
  
    1.  在 \[**應用程式**\] 屬性頁的 \[**目標 Framework**\] 下拉式清單中，選取 .NET Framework 3.5。  
  
3.  如果是 Visual Basic 專案，請按一下 \[**專案**\] 功能表，然後按一下 \[**屬性**\]。  
  
    1.  在 \[**編譯**\] 屬性頁中，按一下 \[**進階編譯選項**\]，然後選取 \[**目標 Framework \(所有組態\)**\] 下拉式清單中的 .NET Framework 3.5。  
  
4.  在 \[**專案**\] 功能表中，依序按一下 \[**加入參考**\] 和 \[**.NET**\] 索引標籤、向下捲動至 \[**System.Core**\] 並按一下它，然後按一下 \[**確定**\]。  
  
5.  將 <xref:System.Linq> 的 `using` 指示詞或匯入的命名空間加入至您的原始程式碼檔或專案。  
  
     如需詳細資訊，請參閱 [using 指示詞](../Topic/using%20Directive%20\(C%23%20Reference\).md)或 [如何：加入或移除匯入的命名空間 \(Visual Basic\)](../Topic/How%20to:%20Add%20or%20Remove%20Imported%20Namespaces%20\(Visual%20Basic\).md)。  
  
### 若要啟用 LINQ to DataSet 功能  
  
1.  必要時，請遵循本主題先前的步驟來加入 System.Core.dll 的參考和 System.Linq 的 `using` 指示詞或匯入命名空間。  
  
2.  在 C\# 或 Visual Basic 中，按一下 \[**專案**\] 功能表，然後按一下 \[**加入參考**\]。  
  
3.  在 \[**加入參考**\] 對話方塊中，按一下 \[**.NET**\] 索引標籤 \(如果它不是在最上層的話\)。  向下捲動至 \[**System.Data**\] 和 \[**System.Data.DataSetExtensions**\]，然後按一下這些項目。  按一下 \[**確定**\] 按鈕。  
  
4.  將 <xref:System.Data> 的 `using` 指示詞或匯入的命名空間加入至您的原始程式碼檔或專案。  如需詳細資訊，請參閱 [using 指示詞](../Topic/using%20Directive%20\(C%23%20Reference\).md)或 [如何：加入或移除匯入的命名空間 \(Visual Basic\)](../Topic/How%20to:%20Add%20or%20Remove%20Imported%20Namespaces%20\(Visual%20Basic\).md)。  
  
5.  針對 LINQ to Dataset 功能，加入 System.Data.DataSetExtensions.dll 的參考。  如果 System.Data.dll 的參考原本不存在，請加入這項參考。  
  
6.  或者，根據您連接至資料庫的方式，加入 `System.Data.Common` 或 `System.Data.SqlClient` 的 `using` 指示詞或匯入的命名空間。  
  
## 請參閱  
 [使用者入門](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)   
 [Getting Started with LINQ](http://msdn.microsoft.com/zh-tw/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)