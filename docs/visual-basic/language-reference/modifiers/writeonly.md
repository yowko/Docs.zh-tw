---
title: "WriteOnly (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "WriteOnly"
  - "vb.WriteOnly"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "write-only properties"
  - "WriteOnly keyword"
  - "sensitive data, protecting"
  - "properties [Visual Basic], write-only"
  - "sensitive data"
ms.assetid: 488d2899-b09f-4cee-92f0-6f9f9fc4f944
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# WriteOnly (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定可寫入但無法讀取的屬性。  
  
## 備註  
  
## 規則  
 **宣告內容：** 只能在模組層級使用 `WriteOnly`。  這表示 `WriteOnly` 屬性的宣告內容必須是類別、結構或模組，且不可以是原始程式檔、命名空間或程序。  
  
 可將屬性宣告為 `WriteOnly`，但不可是變數。  
  
## 使用 WriteOnly 的時機  
 您有時會想要使用程式碼能夠設定值，但卻找不到它是什麼。  例如，敏感資料 \(例如社會註冊碼或密碼\) 需要加以保護，讓任何未設定它的元件無法進行存取。  在這些情況下，可使用 `WriteOnly` 屬性來設定該值。  
  
> [!IMPORTANT]
>  定義和使用 `WriteOnly` 屬性時，請考慮下列其他的保護措施：  
  
-   **覆寫** 如果屬性是類別的成員，則容許將它預設成 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)，且不會將它宣告為 `Overridable` 或 `MustOverride`。  這會讓衍生類別無法透過覆寫進行不良的存取。  
  
-   **存取層級** 如果將屬性的敏感資料保留在一個或多個變數中，請將此資料宣告為 [Private](../../../visual-basic/language-reference/modifiers/private.md)，這樣就沒有其他程式碼可進行存取。  
  
-   **加密** ：以加密格式 \(而非純文字\) 儲存所有敏感資料。  如果惡意程式碼以某種方法取得該記憶體區域的存取權，則使用此資料會較困難。  如果需要序列化敏感資料，則加密也十分有用。  
  
-   **重設** ：正在結束定義屬性的類別、結構或模組時，請將敏感資料重設為預設值，或重設為其他不具意義的值。  釋出記憶體區域以供一般存取時，這會提供額外的保護。  
  
-   **保存性** ：如果可以避免，請不要保存任何敏感資料 \(例如保留在磁碟上\)。  而且，請不要將任何敏感資料寫入剪貼簿。  
  
 `WriteOnly` 修飾詞可用於以下內容中：  
  
 [Property Statement](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## 請參閱  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)   
 [Private](../../../visual-basic/language-reference/modifiers/private.md)   
 [關鍵字](../../../visual-basic/language-reference/keywords/index.md)