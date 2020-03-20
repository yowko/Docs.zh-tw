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
ms.openlocfilehash: a9afa0db516a542b74d08a4c3754a3244abbbea7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153773"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<使用隨機字串雜湊演算法>元素
確定通用語言運行時是否根據每個應用程式域計算字串的雜湊代碼。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<使用隨機字串雜湊演算法>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<UseRandomizedStringHashAlgorithm
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定字串的雜湊代碼是否根據應用程式域計算。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`0`|通用語言運行時不根據每個應用程式域計算字串的雜湊代碼;因此，不計算字串的雜湊代碼。單個演算法用於計算字串雜湊代碼。 這是預設值。|  
|`1`|通用語言運行時根據每個應用程式域計算字串的雜湊代碼。 不同應用程式域和不同進程中的相同字串將具有不同的雜湊代碼。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 預設情況下，<xref:System.StringComparer>類<xref:System.String.GetHashCode%2A?displayProperty=nameWithType>和方法使用單個雜湊演算法，該演算法跨應用程式域生成一致的雜湊代碼。 這相當於將`enabled``<UseRandomizedStringHashAlgorithm>`元素的屬性設置為`0`。 這是 .NET 框架 4 中使用的雜湊演算法。  
  
 類<xref:System.StringComparer>和方法<xref:System.String.GetHashCode%2A?displayProperty=nameWithType>還可以使用不同的雜湊演算法，該演算法根據每個應用程式域計算雜湊代碼。 因此，等效字串的雜湊代碼將因應用程式域而異。 這是一個加入宣告功能;要利用它，必須將`enabled``<UseRandomizedStringHashAlgorithm>`元素的屬性設置為`1`。  
  
 雜湊表中的字串查找通常是 O（1） 操作。 但是，當發生大量衝突時，查找可能會成為 O（n<sup>2</sup>） 操作。 您可以使用`<UseRandomizedStringHashAlgorithm>`配置元素生成每個應用程式域的隨機雜湊演算法，從而限制潛在衝突的數量，尤其是當計算雜湊代碼的鍵基於使用者輸入的資料時。  
  
## <a name="example"></a>範例  
 下面的示例定義一個`DisplayString`類，該類包含私有字串常量`s`，其值為"這是一個字串"。 它也包含 `ShowStringHashCode` 方法，這個方法會將字串值及其雜湊碼與方法執行所在之應用程式定義域的名稱一起顯示。  
  
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
