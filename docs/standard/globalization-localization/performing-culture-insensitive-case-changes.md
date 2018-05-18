---
title: 執行不區分文化特性的大小寫變更
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f560e3b080f6355d4e0c433c2a2218fbcbc6d72
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="performing-culture-insensitive-case-changes"></a>執行不區分文化特性的大小寫變更
<xref:System.String.ToUpper%2A?displayProperty=nameWithType>、<xref:System.String.ToLower%2A?displayProperty=nameWithType>、<xref:System.Char.ToUpper%2A?displayProperty=nameWithType> 和 <xref:System.Char.ToLower%2A?displayProperty=nameWithType> 方法提供不接受任何參數的多載。 根據預設，不含參數的這些多載會根據 <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> 的值，執行大小寫變更。 這會產生可能會因為文化特性而有所不同的區分大小寫結果。 若要釐清您希望大小寫變更是區分文化特性還是不區分文化特性，就應該使用要求您明確地指定 `culture` 參數的這些方法的多載。 針對區分文化特性的大小寫變更，請為 `culture` 參數指定 `CultureInfo.CurrentCulture`。 至於不區分文化特性的大小寫變更，則為 `culture` 參數指定 `CultureInfo.InvariantCulture`。  
  
 字串通常會轉換為標準大小寫，讓之後能夠更輕鬆地查閱。 以這種方式使用字串時，您應該為 `culture` 參數指定 `CultureInfo.InvariantCulture`，因為 <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> 的值在變更大小寫的時間與發生查閱的時間之間可能會有所變更。  
  
 如果安全性決策必須以大小寫變更作業為基礎，則作業應該不區分文化特性，以確保結果不受 `CultureInfo.CurrentCulture` 的值影響。 如需示範區分文化特性的字串作業如何產生不一致結果的範例，請參閱[使用字串的最佳做法](../../../docs/standard/base-types/best-practices-strings.md)一文中的＜使用目前文化特性的字串比較＞一節。  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a>使用 String.ToUpper 和 String.ToLower 方法  
 為使程式碼更清楚，建議您務必使用 `String.ToUpper` 和 `String.ToLower` 方法的多載，讓您明確地指定 `culture` 參數。 例如，下列程式碼會執行識別碼查閱。 `key.ToLower` 作業預設為區分文化特性，但讀取程式碼時，這種行為並不明確。  
  
### <a name="example"></a>範例  
  
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
  
 如果您希望 `key.ToLower` 作業是不區分文化特性，則應該如下所示變更上述範例，才能在變更大小寫時，明確地使用 `CultureInfo.InvariantCulture`。  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a>使用 Char.ToUpper 和 Char.ToLower 方法  
 雖然 `Char.ToUpper` 和 `Char.ToLower` 方法具有與 `String.ToUpper` 和 `String.ToLower` 方法相同的特性，但是受到影響的文化特性只有土耳其文 (土耳其) 和亞塞拜然文 (拉丁，亞塞拜然)。 這些是具有單一字元大小寫差異的唯二文化特性。 如需這個特殊案例對應的詳細資訊，請參閱 <xref:System.String> 類別主題中的＜大小寫＞一節。 為使程式碼更清楚並確保一致性的結果，建議您務必使用這些方法的多載，讓您明確地指定 `culture` 參數。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
 [執行不區分文化特性的字串作業](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
