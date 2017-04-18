---
title: "HOW TO：驗證 DBML 和外部對應檔案 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d9ea37f5-0a9e-4401-8fc3-1e6fd44c49f9
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# HOW TO：驗證 DBML 和外部對應檔案
如果修改外部對應檔案和 .dbml 檔案，則必須根據它們各自的結構描述定義進行驗證。  這個主題提供實作驗證流程的步驟，供 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] 使用者使用。  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
### 若要驗證 .dbml 或 XML 檔案  
  
1.  在 Visual Studio \[**檔案**\] 功能表上，指向 \[**開啟舊檔**\]，然後按一下 \[**檔案**\]。  
  
2.  在 \[**開啟檔案**\] 對話方塊中，按一下想要驗證的 .dbml 或 XML 對應檔案。  
  
     這個檔案會在 \[**XML 編輯器**\] 中開啟。  
  
3.  以滑鼠右鍵按一下這個視窗，然後按一下 \[**屬性**\]。  
  
4.  按一下 \[**屬性**\] 視窗中 \[**Schemas**\] 屬性的省略符號。  
  
     \[**XML 結構描述**\] 對話方塊隨即開啟。  
  
5.  請記下適用於您目的的適當結構描述定義。  
  
    -   DbmlSchema.xsd 是用來驗證 .dbml 檔案的結構描述定義。  如需詳細資訊，請參閱[LINQ to SQL 的程式碼產生](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)。  
  
    -   LinqToSqlMapping.xsd 是用來驗證外部 XML 對應檔案的結構描述定義。  如需詳細資訊，請參閱[外部對應](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)。  
  
6.  在所要結構描述定義資料列的 \[**使用**\] 資料行中，按一下以開啟下拉式方塊，然後按一下 \[**使用這個結構描述**\]。  
  
     結構描述定義檔案現在已經與 DBML 或 XML 對應檔案產生關聯。  
  
     請確定未選取其他結構描述定義。  
  
7.  在 \[**檢視**\] 功能表上，按一下 \[**錯誤清單**\]。  
  
     判斷是否已產生錯誤、警告或訊息。  如果未產生，則會根據結構描述定義驗證 XML 檔案為有效。  
  
## 提供結構描述定義的替代方法  
 如果適用的 .xsd 檔案因某種原因而未出現在 \[**XML 結構描述**\] 對話方塊中，則可以從 \[說明\] 主題中下載 .xsd 檔案。  下列步驟可幫助您以 Unicode 格式儲存下載的檔案，而這種格式是 [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] XML 編輯器需要的格式。  
  
#### 若要從說明主題中複製結構描述定義檔案  
  
1.  如這個主題前面所述，找到內含結構描述定義的 \[說明\] 主題。  
  
    -   如需 .dbml 檔案，請參閱 [LINQ to SQL 的程式碼產生](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)。  
  
    -   如需外部對應檔案，請參閱[外部對應](../../../../../../docs/framework/data/adonet/sql/linq/external-mapping.md)。  
  
2.  按一下 \[**複製程式碼**\]，將程式碼檔案複製至 \[剪貼簿\]。  
  
3.  啟動 \[記事本\]，建立新的檔案。  
  
4.  將剪貼簿中的程式碼貼入 \[記事本\] 檔案中。  
  
5.  按一下 \[記事本\] 的 \[**檔案**\] 功能表，然後按一下 \[**另存新檔**\]。  
  
6.  選取 \[**編碼**\] 方塊中的 \[**Unicode**\]。  
  
    > [!IMPORTANT]
    >  這個選項可確保會在文字檔前面加上 Unicode 16 位元組順序標記 \(`FFFE`\)。  
  
7.  在 \[**檔名**\] 方塊中，建立副檔名為 .xsd 的檔名。  
  
## 請參閱  
 [參考資料](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)