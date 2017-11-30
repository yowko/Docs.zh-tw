---
title: "&lt;UseRandomizedStringHashAlgorithm&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- UseRandomizedStringHashAlgorithm element
- <UseRandomizedStringHashAlgorithm> element
ms.assetid: c08125d6-56cc-4b23-b482-813ff85dc630
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 7cd561cf0e0a9e080b150bdaa412686126423c91
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltuserandomizedstringhashalgorithmgt-element"></a>&lt;UseRandomizedStringHashAlgorithm&gt;項目
決定 common language runtime 是否計算字串的雜湊程式碼上每個應用程式定義域做為基準。  
  
 \<configuration>  
\<執行階段 >  
\<UseRandomizedStringHashAlgorithm >  
  
## <a name="syntax"></a>語法  
  
```xml  
<UseRandomizedStringHashAlgorithm   
   enabled=0|1 />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定字串的雜湊程式碼會對計算每個應用程式定義域做為基準。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|說明|  
|-----------|-----------------|  
|`0`|Common language runtime 不會計算字串的雜湊程式碼在每個應用程式網域為基礎;單一演算法用來計算字串的雜湊碼。 這是預設值。|  
|`1`|通用語言執行平台計算雜湊碼的字串上每個應用程式定義域做為基準。 不同的程序和不同的應用程式定義域中的相同字串將會有不同的雜湊碼。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 根據預設，<xref:System.StringComparer>類別和<xref:System.String.GetHashCode%2A?displayProperty=nameWithType>方法使用單一的雜湊演算法產生一致的雜湊程式碼在應用程式定義域。 這相當於設定`enabled`屬性`<UseRandomizedStringHashAlgorithm>`元素`0`。 這是雜湊演算法中使用[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]。  
  
 <xref:System.StringComparer>類別和<xref:System.String.GetHashCode%2A?displayProperty=nameWithType>方法也可以使用不同的雜湊演算法可計算雜湊程式碼在每個應用程式定義域做為基準。 如此一來，雜湊碼的對等的字串會跨應用程式定義域的不同。 這是選擇性功能。若要充分利用它，您必須設定`enabled`屬性`<UseRandomizedStringHashAlgorithm>`元素`1`。  
  
 字串中的查閱雜湊資料表通常是一種 o （1） 運算。 不過，大量的衝突發生時，查詢可能會變成 O (n<sup>2</sup>) 作業。 您可以使用`<UseRandomizedStringHashAlgorithm>`組態項目，以產生隨機的雜湊演算法，每個應用程式網域，接著將衝突的可能性，數目限制，特別是當計算出雜湊程式碼的索引鍵會根據資料輸入由使用者。  
  
## <a name="example"></a>範例  
 下列範例會定義`DisplayString`類別，其中包含私用的字串常數， `s`，其值為"This is 字串"。 它也包含`ShowStringHashCode`方法顯示的字串值和其雜湊程式碼，以及執行此方法的應用程式定義域的名稱。  
  
 [!code-csharp[System.String.GetHashCode#2](../../../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.String.GetHashCode/CS/perdomain.cs#2)]
 [!code-vb[System.String.GetHashCode#2](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.String.GetHashCode/VB/perdomain.vb#2)]  
  
 當您執行範例但不提供組態檔時，它會顯示與下列類似的輸出。 請注意，雜湊碼的字串完全相同的兩個應用程式定義域中。  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 941BCEAC  
String 'This is a string.' in domain 'NewDomain': 941BCEAC  
```  
  
 不過，如果您將下列組態檔加入至範例目錄，然後執行範例應用程式定義域將不同的雜湊程式碼相同的字串。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <UseRandomizedStringHashAlgorithm enabled="1" />  
   </runtime>  
</configuration>  
```  
  
 組態檔時，此範例會顯示下列輸出：  
  
```  
String 'This is a string.' in domain 'PerDomain.exe': 5435776D  
String 'This is a string.' in domain 'NewDomain': 75CC8236  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.String.GetHashCode%2A?displayProperty=nameWithType>  
 <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
