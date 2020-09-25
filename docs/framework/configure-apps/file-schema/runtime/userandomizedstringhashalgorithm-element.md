---
title: <UseRandomizedStringHashAlgorithm> 項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
ms.openlocfilehash: 148d55c8b8a63737867c4bfdf3ab118dfdefd6f9
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174091"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<UseRandomizedStringHashAlgorithm> 項目

判斷 common language runtime 是否針對每個應用程式域計算字串的雜湊碼。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<UseRandomizedStringHashAlgorithm>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定是否針對每個應用程式域計算字串的雜湊碼。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`0`|Common language runtime 不會針對每個應用程式域計算字串的雜湊碼。單一演算法用來計算字串雜湊碼。 此為預設值。|  
|`1`|Common language runtime 會根據每個應用程式域來計算字串的雜湊碼。 不同的應用程式域和不同進程中的相同字串將會有不同的雜湊碼。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  

 根據預設， <xref:System.StringComparer> 類別和 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> 方法會使用單一雜湊演算法，在應用程式域之間產生一致的雜湊程式碼。 這相當於將元素的 `enabled` 屬性設定 `<UseRandomizedStringHashAlgorithm>` 為 `0` 。 這是 .NET Framework 4 中使用的雜湊演算法。  
  
 <xref:System.StringComparer>類別和 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType> 方法也可以使用不同的雜湊演算法來計算每個應用程式域的雜湊碼。 因此，對等字串的雜湊程式碼將會在應用程式域之間有所不同。 這是加入宣告的功能;若要利用它，您必須將元素的 `enabled` 屬性設定 `<UseRandomizedStringHashAlgorithm>` 為 `1` 。  
  
 雜湊表中的字串查閱通常是 O (1) 作業。 不過，當發生大量衝突時，查閱可能會變成 O (n<sup>2</sup>) 作業。 您可以使用 `<UseRandomizedStringHashAlgorithm>` configuration 元素來產生每個應用程式網域的隨機雜湊演算法，進而限制潛在衝突的數目，特別是當雜湊碼的計算索引鍵是根據使用者輸入的資料輸入時。  
  
## <a name="example"></a>範例  

 下列範例 `DisplayString` 會定義包含私用字串常數的類別， `s` 其值為 "This 是 string"。 它也包含 `ShowStringHashCode` 方法，這個方法會將字串值及其雜湊碼與方法執行所在之應用程式定義域的名稱一起顯示。  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 當您在沒有提供組態檔的情況下執行此範例，它會顯示類似下列的輸出。 請注意，字串的雜湊碼在兩個應用程式定義域中相同。  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 不過，如果您將下列組態檔加入至範例的目錄，然後執行這個範例，相同字串的雜湊碼將會因為應用程式定義域不同而有所不同。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 當組態檔存在時，這個範例會顯示下列輸出：  
  
```console
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
