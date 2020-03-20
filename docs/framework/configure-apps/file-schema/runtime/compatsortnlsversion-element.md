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
ms.openlocfilehash: 30afeb2ab9380db75cbeb723ea15a23e4313c9e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154266"
---
# <a name="compatsortnlsversion-element"></a>\<比較排序NLSversion>元素
指定執行階段在執行字串比較時，應使用舊版排序次序。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<運行時>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<比較>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<CompatSortNLSVersion
   enabled="4096"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定要使用其排序次序的地區設定 ID。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|4096|表示替代排序次序的地區設定 ID。 在這種情況下，4096 表示 .NET 框架 3.5 和早期版本的排序次序。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關執行階段初始化選項的資訊。|  
  
## <a name="remarks"></a>備註  
 由於在 .NET 框架 4 中由<xref:System.Globalization.CompareInfo?displayProperty=nameWithType>類執行的字串比較、排序和套管操作符合 Unicode 5.1 標準，因此字串比較<xref:System.String.Compare%28System.String%2CSystem.String%29?displayProperty=nameWithType>方法<xref:System.String.LastIndexOf%28System.String%29?displayProperty=nameWithType>的結果（如 和）可能與 .NET Framework 的早期版本不同。 如果應用程式依賴于舊行為，則可以通過將`<CompatSortNLSVersion>`元素包括在應用程式的設定檔中來還原 .NET Framework 3.5 和早期版本中使用的字串比較和排序規則。  
  
> [!IMPORTANT]
> 還原舊版字串比較和排序規則也必須要有可在本機系統上提供的 sort00001000.dll 動態連結程式庫。  
  
 您也可以在建立應用程式定義域時，將字串 "NetFx40_Legacy20SortingBehavior" 傳遞給 <xref:System.AppDomainSetup.SetCompatibilitySwitches%2A> 方法，這樣做就可以在特定應用程式定義域中使用舊版字串排序和比較規則。  
  
## <a name="example"></a>範例  
 下列範例會將兩個 <xref:System.String> 物件具現化，並呼叫 <xref:System.String.Compare%28System.String%2CSystem.String%2CSystem.StringComparison%29?displayProperty=nameWithType> 方法以使用目前文化特性的慣例比較這兩個物件。  
  
 [!code-csharp[String.BreakingChanges#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/string.breakingchanges/cs/example1.cs#1)]
 [!code-vb[String.BreakingChanges#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/string.breakingchanges/vb/example1.vb#1)]  
  
 在 .NET 框架 4 上運行示例時，將顯示以下輸出：
  
```console
sta follows a in the sort order.  
```  
  
 這與在 .NET Framework 3.5 上運行示例時顯示的輸出完全不同：
  
```console
sta equals a in the sort order.  
```  
  
 但是，如果將以下設定檔添加到示例的目錄中，然後在 .NET Framework 4 上運行示例，則輸出與在 .NET Framework 3.5 上運行時的示例生成的輸出相同。  
  
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
