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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49b53dcd4db7e0ac1e9079e763b8ed76c1088e0e
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252194"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<UseRandomizedStringHashAlgorithm > 元素
判斷 common language runtime 是否會針對每個應用程式網域, 計算字串的雜湊碼。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<UseRandomizedStringHashAlgorithm>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定是否要根據每個應用程式域來計算字串的雜湊碼。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`0`|通用語言執行平臺不會針對每個應用程式網域來計算字串的雜湊碼。單一演算法用來計算字串雜湊碼。 這是預設值。|  
|`1`|通用語言執行時間會針對每個應用程式網域, 計算字串的雜湊碼。 不同應用程式域和不同進程中的相同字串會有不同的雜湊碼。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 根據預設, <xref:System.StringComparer>類別<xref:System.String.GetHashCode%2A?displayProperty=nameWithType>和方法會使用單一雜湊演算法, 在應用程式域之間產生一致的雜湊碼。 這相當於將`enabled` `<UseRandomizedStringHashAlgorithm>`元素的屬性設定為`0`。 這是 .NET Framework 4 中使用的雜湊演算法。  
  
 <xref:System.StringComparer> 類別<xref:System.String.GetHashCode%2A?displayProperty=nameWithType>和方法也可以使用不同的雜湊演算法, 根據每個應用程式域來計算雜湊碼。 因此, 對等字串的雜湊碼會在應用程式域之間有所不同。 這是可加入宣告的功能;若要利用它, 您必須將`enabled` `<UseRandomizedStringHashAlgorithm>`元素的屬性設定為`1`。  
  
 雜湊表中的字串查詢通常是 O (1) 運算。 不過, 當發生大量衝突時, 查閱可能會變成 O (n<sup>2</sup>) 運算。 您可以使用`<UseRandomizedStringHashAlgorithm>` configuration 專案來產生每個應用程式域的隨機雜湊演算法, 進而限制可能發生衝突的數目, 特別是在計算雜湊碼的索引鍵時, 會根據資料輸入由使用者。  
  
## <a name="example"></a>範例  
 下列範例會定義`DisplayString`包含私用字串`s`常數的類別, 其值為 "This is a string"。 它也包含一個`ShowStringHashCode`方法, 它會顯示字串值和其雜湊碼, 以及方法執行所在之應用程式域的名稱。  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 當您執行範例但未提供設定檔時, 它會顯示類似下列的輸出。 請注意, 字串的雜湊碼在兩個應用程式域中都相同。  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 不過, 如果您將下列設定檔新增至範例的目錄, 然後執行範例, 則相同字串的雜湊碼將會因應用程式域而有所不同。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 當設定檔存在時, 此範例會顯示下列輸出:  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
