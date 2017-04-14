---
title: "執行不區分文化特性的大小寫變更 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "String.ToLower 方法"
  - "文化特性，區分大小寫"
  - "Char.ToLower 方法"
  - "大小寫，不區分文化特性的字串變更"
  - "Char.ToUpper 方法"
  - "不區分文化特性的字串作業，大小寫變更"
  - "String.ToUpper 方法"
  - "文化特性參數"
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
caps.latest.revision: 18
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 18
---
# 執行不區分文化特性的大小寫變更
<xref:System.String.ToUpper%2A?displayProperty=fullName>、<xref:System.String.ToLower%2A?displayProperty=fullName>、<xref:System.Char.ToUpper%2A?displayProperty=fullName> 和 <xref:System.Char.ToLower%2A?displayProperty=fullName> 方法提供不接受任何參數的多載。  在預設情況下，這些沒有參數的多載會根據 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName> 的值執行大小寫變更。  這會產生可能因文化特性而異的區分大小寫結果。  無論您要讓大小寫變更成為區分文化特性或是不區分文化特性，為了讓目的更清楚，您應該使用這些方法 \(需要您明確指定 `culture` 參數\) 的多載。  若要進行區分文化特性的大小寫變更，請指定 `CultureInfo.CurrentCulture` 做為 `culture` 參數。  若要進行不區分文化特性的大小寫變更，請指定 `CultureInfo.InvariantCulture` 做為 `culture` 參數。  
  
 通常字串會轉換為標準大小寫以方便日後查閱。  當字串以這種方式使用時，您應該指定 `CultureInfo.InvariantCulture` 做為 `culture` 參數，因為在大小寫變更到查閱執行之間，<xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=fullName> 的值可能會有變更。  
  
 如果是根據大小寫變更作業進行安全性決策，則作業應該不區分文化特性，以確保結果不受 `CultureInfo.CurrentCulture` 的值影響。  如需符合文化特性的字串運算如何產生不一致結果的範例，請參閱[使用字串的最佳作法](../../../docs/standard/base-types/best-practices-strings.md)的＜使用目前文化特性的字串比較＞一節。  
  
## 使用 String.ToUpper 和 String.ToLower 方法  
 為了使程式碼更為明確，建議您一律使用 `String.ToUpper` 和 `String.ToLower` 方法的多載，讓您可以明確指定 `culture` 參數。  例如，下列程式碼會執行識別項查詢。  `key.ToLower` 作業會在預設情況下區分文化特性，但從程式碼的閱讀中，並無法清楚得知這樣的行為。  
  
### 範例  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 如果想讓 `key.ToLower` 作業不區分文化特性，應該將上述範例變更如下，以便在變更大小寫時，明確使用 `CultureInfo.InvariantCulture`。  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
  
```  
  
```csharp  
static object LookupKey(string key)   
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## 使用 Char.ToUpper 和 Char.ToLower 方法  
 雖然 `Char.ToUpper` 和 `Char.ToLower` 方法具有與 `String.ToUpper` 和 `String.ToLower` 方法相同的特性，但是受到影響的文化特性只有土耳其文 \(土耳其\) 和亞塞拜然文 \(拉丁，亞塞拜然\)。  這是僅有的兩個具有單一字元大小寫差異的文化特性。  如需這個特殊案例的對應細節，請參閱 <xref:System.String> 類別主題中的 \< 畫面格 \> 一節。  為了使程式碼更為明確及確保結果一致，建議您一律使用這些方法的多載，以便能夠明確指定 `culture` 參數。  
  
## 請參閱  
 <xref:System.String.ToUpper%2A?displayProperty=fullName>   
 <xref:System.String.ToLower%2A?displayProperty=fullName>   
 <xref:System.Char.ToUpper%2A?displayProperty=fullName>   
 <xref:System.Char.ToLower%2A?displayProperty=fullName>   
 [執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)