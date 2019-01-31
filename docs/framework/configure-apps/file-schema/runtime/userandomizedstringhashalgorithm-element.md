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
ms.openlocfilehash: 3545938d8f9a59c8f3c6d03e5e67bb5f545a4981
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55260589"
---
# <a name="userandomizedstringhashalgorithm-element"></a>\<UseRandomizedStringHashAlgorithm > 項目
判斷 common language runtime 是否會計算字串的雜湊碼，在每個應用程式定義域為基準。  
  
 \<configuration>  
\<執行階段 >  
\<UseRandomizedStringHashAlgorithm>  
  
## <a name="syntax"></a>語法  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定是否計算字串的雜湊碼，以在每個應用程式定義域為基準。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`0`|Common language runtime 不會計算字串的雜湊碼在每個應用程式網域進行;單一的演算法用來計算字串的雜湊碼。 這是預設值。|  
|`1`|Common language runtime 計算字串的雜湊碼在每個應用程式定義域為基準。 相同的字串，在不同的應用程式定義域和不同的處理序中會有不同的雜湊碼。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 根據預設，<xref:System.StringComparer>類別和<xref:System.String.GetHashCode%2A?displayProperty=nameWithType>方法使用單一的雜湊演算法可跨應用程式定義域產生一致雜湊碼。 這相當於設定`enabled`的屬性`<UseRandomizedStringHashAlgorithm>`項目`0`。 這是用於雜湊演算法[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]。  
  
 <xref:System.StringComparer>類別和<xref:System.String.GetHashCode%2A?displayProperty=nameWithType>方法也可以使用不同的雜湊演算法來計算雜湊程式碼在每個應用程式定義域為基準。 如此一來，對等字串的雜湊程式碼會在應用程式定義域而有所不同。 這是選用的功能;若要充分利用它，您必須設定`enabled`的屬性`<UseRandomizedStringHashAlgorithm>`項目`1`。  
  
 雜湊表中的字串查閱通常是 o （1） 的作業。 不過，當發生大量碰撞，查閱可能會變成 O (n<sup>2</sup>) 作業。 您可以使用`<UseRandomizedStringHashAlgorithm>`組態項目來產生隨機的雜湊演算法，每個應用程式定義域，進而限制可能發生的衝突數目，特別是當導出的雜湊碼的索引鍵為基礎的資料輸入由使用者。  
  
## <a name="example"></a>範例  
 下列範例會定義`DisplayString`類別，其中包含私用的字串常數， `s`，其值為"This is 字串"。 它也包含`ShowStringHashCode`方法，以顯示的字串值和其雜湊程式碼，以及用來執行此方法的應用程式定義域的名稱。  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 當您執行範例，而不需要提供組態檔時，它會顯示類似下列的輸出。 請注意，字串的雜湊碼相同的兩個應用程式定義域中。  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 不過，如果您將下列組態檔新增至範例的目錄，然後執行範例的相同字串的雜湊碼將會因應用程式定義域。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 當組態檔存在時，此範例會顯示下列輸出：  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>另請參閱
- <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
