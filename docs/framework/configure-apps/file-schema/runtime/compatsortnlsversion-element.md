---
title: <CompatSortNLSVersion> 項目
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 575d44ad9ecf445ba5d4b7fbe47032127ccb33ae
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252725"
---
# <a name="compatsortnlsversion-element"></a>\<CompatSortNLSVersion > 元素
指定執行階段在執行字串比較時，應使用舊版排序次序。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<執行時間 >** ](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<CompatSortNLSVersion>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定要使用其排序次序的地區設定 ID。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|4096|表示替代排序次序的地區設定 ID。 在此情況下，4096代表 .NET Framework 3.5 及舊版的排序次序。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 由於 .NET Framework 4 中的類別所<xref:System.Globalization.CompareInfo?displayProperty=nameWithType>執行的字串比較、排序和大小寫作業符合 Unicode 5.1 標準，因此字串比較方法<xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType> （例如和<xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType> ）的結果可能會與舊版的 .NET Framework。 如果您的應用程式相依于舊版行為，您可以在應用程式的設定檔中包含`<CompatSortNLSVersion>`專案，以還原 .NET Framework 3.5 和更早版本中使用的字串比較和排序規則。  
  
> [!IMPORTANT]
> 還原舊版字串比較和排序規則也必須要有可在本機系統上提供的 sort00001000.dll 動態連結程式庫。  
  
 您也可以在建立應用程式定義域時，將字串 "NetFx40_Legacy20SortingBehavior" 傳遞給 <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> 方法，這樣做就可以在特定應用程式定義域中使用舊版字串排序和比較規則。  
  
## <a name="example"></a>範例  
 下列範例會將兩個 <xref:System.String> 物件具現化，並呼叫 <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法以使用目前文化特性的慣例比較這兩個物件。  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 當您執行 .NET Framework 4 上的範例時，它會顯示下列輸出。  
  
```  
sta follows a in the sort order.  
```  
  
 這與您在 .NET Framework 3.5 上執行範例時所顯示的輸出完全不同。  
  
```  
sta equals a in the sort order.  
```  
  
 不過，如果您將下列設定檔新增至範例的目錄，然後在 .NET Framework 4 上執行範例，則輸出會與範例在 .NET Framework 3.5 上執行時所產生的相同。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
