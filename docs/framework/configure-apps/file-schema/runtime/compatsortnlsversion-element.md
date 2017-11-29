---
title: "&lt;CompatSortNLSVersion&gt;項目"
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
- <CompatSortNLSVersion> element
- CompatSortNLSVersion element
ms.assetid: 782cc82e-83f7-404a-80b7-6d3061a8b6e3
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8d82187248e743d9081a97411f2ff2ad84707e61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompatsortnlsversiongt-element"></a>&lt;CompatSortNLSVersion&gt;項目
指定執行階段在執行字串比較時，應使用舊版排序次序。  
  
 \<configuration>  
\<執行階段 >  
\<CompatSortNLSVersion > 項目  
  
## <a name="syntax"></a>語法  
  
```xml  
<CompatSortNLSVersion    
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定要使用其排序次序的地區設定 ID。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|4096|表示替代排序次序的地區設定 ID。 在這個案例中，4096 表示 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] (含) 以前版本的排序次序。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 因為由執行字串比較、 排序和大小寫作業<xref:System.Globalization.CompareInfo?displayProperty=nameWithType>類別[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]例如符合 Unicode 5.1 標準，字串比較方法結果<xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType>和<xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType>可能不同舊版.NET Framework 中。 如果您的應用程式依賴舊版的行為，您可以藉由在應用程式的組態檔中包含 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 項目的方式，還原 `<CompatSortNLSVersion>` (含) 以前版本中使用的字串比較和排序規則。  
  
> [!IMPORTANT]
>  還原舊版字串比較和排序規則也必須要有可在本機系統上提供的 sort00001000.dll 動態連結程式庫。  
  
 您也可以在建立應用程式定義域時，將字串 "NetFx40_Legacy20SortingBehavior" 傳遞給 <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> 方法，這樣做就可以在特定應用程式定義域中使用舊版字串排序和比較規則。  
  
## <a name="example"></a>範例  
 下列範例會將兩個 <xref:System.String> 物件具現化，並呼叫 <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法以使用目前文化特性的慣例比較這兩個物件。  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 當您在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 上執行範例時，會顯示下列輸出。  
  
```  
sta follows a in the sort order.  
```  
  
 這與您在 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 上執行範例時顯示的輸出完全不同。  
  
```  
sta equals a in the sort order.  
```  
  
 不過，如果您將下列組態檔加入範例的目錄中，然後在 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 上執行該範例，則輸出會與在 [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] 上執行範例時所產生的輸出完全相同。  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
   <runtime>  
      <CompatSortNLSVersion enabled="4096"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
