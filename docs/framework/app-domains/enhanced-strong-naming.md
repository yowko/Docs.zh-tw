---
title: "進階強式命名 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "強式命名 [.NET Framework], 加強"
  - "強式名稱組件"
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# 進階強式命名
強式名稱簽章是在 .NET Framework 中用於識別組件的識別機制。  它是公開金鑰數位簽章，通常用來驗證從建立者 \(簽署人\) 傳送給收件者 \(驗證人\) 的資料的完整性。  這個簽章是當做組件的唯一識別使用，確保組件的參考不會模稜兩可。  組件會簽署為建置流程的一部分，然後在載入時驗證。  
  
 強式名稱簽章有助於防止惡意人士竄改組件，然後以原始簽署人的金鑰重新簽署組件。  不過，強式名稱金鑰不包含發行者的任何可靠的資訊，也不包含憑證階層架構。  強式名稱簽章並不保證簽署組件人員的可信度，也不表示該人員是否為金鑰的合法擁有者，僅表示簽署組件之金鑰的擁有者。  因此，我們不建議使用強式名稱簽章做為安全性驗證程式來進行協力廠商程式碼的信任工作。  建議以 Microsoft Authenticode 驗證程式碼。  
  
## 傳統強式名稱的限制  
 在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 之前的版本中使用的強式命名技術有下列缺點：  
  
-   金鑰鍵常遭到攻擊，改良後的技術和硬體可以更容易從公開金鑰推斷出私密金鑰。  若要防範攻擊，就需要較大的金鑰。[!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 之前的 .NET Framework 版本會提供以任何大小之金鑰 \(預設大小為 1024 位元\) 簽署的功能，但是以新的機碼簽署組件會中斷參考組件舊識別的所有二進位檔。  因此，如果您想要維護相容性，升級簽署金鑰的大小是極為困難的工作。  
  
-   強式名稱簽署僅支援 SHA\-1 演算法。  最近發現 SHA\-1 不適合用於安全雜湊應用程式。  因此，需要更強的演算法 \(SHA\-256 或更強大\)。  SHA\-1 可能會遺失其相容的 FIPS ，問題出現在只使用 FIPS 相容軟體和演算法。  
  
## 增強的強式名稱的優點  
 增強的強式名稱的主要優點是，能夠與預先存在的強式名稱相容，以及能夠宣告某一個識別與另一個識別相等：  
  
-   具有既存簽署組件的開發人員可將其身分識別移轉至 SHA\-2 演算法，同時維持與參考舊身分識別組件的相容性。  
  
-   建立新組件但不關心既有強式名稱簽章的開發人員，可以使用更安全的 SHA\-2 演算法，並依照往常的方式簽署組件。  
  
## 使用增強的強式名稱  
 強式名稱金鑰包含簽章金鑰和識別金鑰。  組件是用簽章金鑰簽署，並且以識別金鑰識別。  在 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]之前，這兩個金鑰是相同的。  從 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 開始，識別金鑰與舊版 .NET Framework 中的金鑰保持相同，不過，簽章金鑰會採用更強大的雜湊演算法。  此外，簽章金鑰會簽署的識別金鑰簽署以建立副署。  
  
 <xref:System.Reflection.AssemblySignatureKeyAttribute> 屬性 \(Attribute\) 可讓組件中繼資料針對組件識別使用既有的公開金鑰，如此可讓舊組件參考繼續運作。<xref:System.Reflection.AssemblySignatureKeyAttribute> 屬性會使用副署，確保新簽章金鑰的擁有人也是舊識別金鑰的擁有人。  
  
### 使用 SHA\-2 簽署，不含金鑰移轉  
 從命令提示字元視窗執行下列命令來簽署組件，而不需要移轉強式名稱簽章:  
  
1.  產生新的身分識別金鑰 \(如果需\)。  
  
    ```  
    sn -k IdentityKey.snk  
    ```  
  
2.  擷取身分識別公開金鑰，並指定使用此金鑰簽署時應使用 SHA\-2 演算法。  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3.  使用身分識別公開金鑰檔來延遲簽署組件。  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4.  重新簽署組件與完整的識別金鑰組。  
  
    ```  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### 使用 SHA\-2 簽署，含金鑰移轉  
 從命令提示字元視窗執行下列命令，來簽署有移轉的強式名稱簽章的組件。  
  
1.  產生身分識別和簽章金鑰組 \(如果需要\)。  
  
    ```  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2.  擷取簽章公開金鑰，並指定使用此金鑰簽署時應使用 SHA\-2 演算法。  
  
    ```  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3.  擷取身分識別公開金鑰，此金鑰可決定產生副署的雜湊演算法。  
  
    ```  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4.  產生 <xref:System.Reflection.AssemblySignatureKeyAttribute> 屬性的參數，並將屬性附加至組件。  
  
    ```  
    sn -ac IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  
  
5.  使用身分識別公開金鑰來延遲簽署組件。  
  
    ```  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
  
    ```  
  
6.  使用簽章金鑰組完整簽署組件。  
  
    ```  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## 請參閱  
 [建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)