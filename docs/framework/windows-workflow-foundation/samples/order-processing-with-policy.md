---
title: "使用原則處理訂 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 66833724-dc36-4fad-86b0-59ffeaa3ba6a
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 使用原則處理訂
訂單處理原則範例將示範在 Windows Workflow Foundation \(WF\) 的 [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] 中引入的一些主要功能。下列是 WF 規則引擎的新功能：  
  
-   運算子多載支援。  
  
-   `new` 運算子的支援，以便允許使用者從 WF 規則建立新的物件和陣列。  
  
-   擴充方法的支援，可讓從 WF 規則呼叫擴充方法的使用者經驗與 C\# 程式碼撰寫方式相容。  
  
> [!NOTE]
>  需安裝 [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)] 才能建置及執行此範例。需要 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 才能開啟專案和方案檔。  
  
 此範例示範 `OrderProcessingPolicy` 專案，在此專案中會輸入一份客戶訂單，其中包括可用項目編號清單和郵遞區號。如果兩個項目都正確，訂單便會成功處理，否則，原則會建立錯誤物件，並利用多載 `+` 運算子和預先定義的擴充方法來通知使用者發生錯誤。  
  
> [!NOTE]
>  [!INCLUDE[crabout](../../../../includes/crabout-md.md)]擴充方法的詳細資訊，請參閱 [C\# 3.0 版規則](http://go.microsoft.com/fwlink/?LinkId=95402) \(英文\)。  
  
 此範例是由下列專案所組成：  
  
-   `OrderErrorLibrary`  
  
     `OrderErrorLibrary` 是定義 `OrderError` 和 `OrderErrorCollection` 類別的類別程式庫。`OrderError` 執行個體是在輸入無效輸入時所建立。此類別程式庫也會提供 `OrderErrorCollection` 類別上的擴充方法，此方法會輸出 `OrderErrorCollection` 中所有 `OrderError` 物件上的 `ErrorText` 屬性。  
  
-   `OrderProcessingPolicy`  
  
     `OrderProcessingPolicy` 專案是 WF 主控台應用程式，其中會定義單一 `PolicyFromFile` 活動。此活動有下列規則：  
  
    -   `invalidItemNum`  
  
         這個規則會驗證 1 到 6 之間 \(包括 1 和 6\) 的項目編號。如果項目編號在有效範圍之內，此規則就不會執行任何動作 \(除了列印至主控台\)。如果項目編號不是在 1 到 6 之間，`invalidItemNum` 規則便會執行下列動作：  
  
        1.  建立新的 `OrderError` 物件，並將輸入的項目編號傳遞給它，然後在該物件上設定 `ErrorText` 和 `CustomerName` 屬性。  
  
        2.  建立 `invalidItemNumErrorCollection` 物件。  
  
        3.  將新建立的 `OrderError` 執行個體新增至 `invalidItemNumErrorCollection`。  
  
         這樣便會示範 `new` 運算子的支援，而您可以透過該項支援來產生符合規則的物件。  
  
    -   `invalidZip`  
  
         這個規則會驗證郵遞區號有 5 個數字，而且範圍在 600 到 99998。如果郵遞區號在有效範圍之內，此規則就不會執行任何動作 \(除了列印至主控台\)。如果郵遞區號少於 5 個數字，或者不是在 00600 到 99998 之間，`invalidZip` 規則便會執行下列動作：  
  
        1.  建立 `OrderError` 物件，並將輸入的郵遞區號傳遞給它，然後在該物件上設定 `ErrorText` 和 `CustomerName` 屬性。  
  
        2.  建立 `invalidZipCodeErrorCollection` 物件。  
  
        3.  將新建立的 `OrderError` 執行個體新增至新建立的 `invalidZipCodeErrorCollection`。  
  
         這個規則會再次示範 `new` 運算子的支援，而您可以透過它來產生符合規則的物件。  
  
    -   `displayErrors`  
  
         這個規則會檢查在兩個 `OrderErrorCollection` 物件 \(`invalidItemNumErrorCollection` 和 `invalidIZipCodeErrorCollection`\) 中的先前兩個規則是否有新增任何錯誤。如果有發生錯誤 \(`invalidItemNumErrorCollection` 或 `invalidZipCodeErrorCollection` 不是 `null`\)，規則便會執行下列動作：  
  
        1.  呼叫多載 `+` 運算子，以便將 `invalidItemNumErrorCollection` 和 `invalidZipCodeErrorCollection` 的內容複製到 `invalidOrdersCollection``OrderErrorCollection` 執行個體。  
  
        2.  在 `invalidOrdersCollection` 上呼叫 `PrintOrderErrors` 擴充方法，並輸出 `invalidOrdersCollection` 中所有 `orderError` 物件上的 `ErrorText` 屬性。  
  
 在 `OrderErrorLibrary` 專案中，`OrderErrorCollection` 上的多載運算子 `+` 是定義在 `OrderErrorCollection` 類別中。它會接受兩個 `OrderErrorCollection` 物件，並將它們結合成為一個 `OrderErrorCollection` 物件。  
  
 `PrintOrderErrors` 擴充方法也有定義在 `OrderErrorLibrary` 專案中。擴充方法是新的 C\# 功能，其可讓開發人員將新方法新增至現有 CLR 型別的公用合約，而不需為其衍生類別或重新編譯原始型別。  
  
 執行範例時會出現提示，要求您輸入名稱、要購買之項目的項目編號以及郵遞區號。這份資訊接著會由定義於原則活動中的規則加以驗證。下列是來自此程式的輸出範例。  
  
```  
Please enter your name: John  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 1  
  
Please enter your 5-Digit zip code: 98102  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Thank you for your order, it has been processed.  
  
Workflow Completed  
Another Order? (Y/N): y  
  
Please enter your name: Joel  
  
What would you like to purchase?  
        (1) Vista Ultimate DVD  
        (2) Vista Ultimate Upgrade DVD  
        (3) Vista Home Premium DVD  
        (4) Vista Home Premium Upgrade DVD  
        (5) Vista Home Basic DVD  
        (6) Vista Home Basic Upgrade DVD  
  
Please enter an item number: 8  
  
Please enter your 5-Digit zip code: 0000  
  
        Executing Rule: invalidItemNum  
        Executing Rule: invalidZip  
        Executing Rule: displayErrors  
  
                              Your order contains the following error(s)  
  
Error: No item number found. Please choose an available item.  
Error: Invalid zip code. Please choose a zip code between 00600 and 99998.  
  
Workflow Completed  
Another Order? (Y/N): n  
```  
  
### 若要設定、建置及執行範例  
  
1.  在 [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 中開啟 OrderProcessingPolicy.sln 專案檔。  
  
2.  在此方案中有兩個不同的專案：`OrderErrorLibrary` 和 `OrderProcessingPolicy`。`OrderProcessingPolicy` 專案會使用定義於 `OrderErrorLibrary` 中的類別和方法。  
  
3.  建置所有專案。  
  
4.  按一下 \[**執行**\]。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續：  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄：  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Rules\Policy\OrderProcessingPolicy`  
  
## 請參閱