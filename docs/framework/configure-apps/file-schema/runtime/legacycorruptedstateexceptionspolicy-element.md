---
title: <legacyCorruptedStateExceptionsPolicy> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: f36e27a1b85cff2ba8c7e838bace37890a5aa760
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151203"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a>\<legacyCorruptedStateExceptionsPolicy> 項目

指定 common language runtime 是否允許 managed 程式碼攔截存取違規和其他損毀狀態例外狀況。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`enabled`|必要屬性。<br /><br /> 指定應用程式將會攔截損毀狀態例外狀況失敗，例如存取違規。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|`false`|應用程式不會攔截損毀狀態例外狀況失敗，例如存取違規。 此為預設值。|  
|`true`|應用程式將會攔截損毀狀態例外狀況失敗，例如存取違規。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  

 在 .NET Framework 3.5 版和更舊版本中，common language runtime 允許 managed 程式碼攔截因進程狀態損毀而引發的例外狀況。 存取違規是這種例外狀況類型的範例。  
  
 從 .NET Framework 4 開始，managed 程式碼不會再于區塊中攔截這些例外狀況類型 `catch` 。 不過，您可以覆寫這項變更，並以兩種方式維護損毀狀態例外狀況的處理：  
  
- 將 `<legacyCorruptedStateExceptionsPolicy>` 元素的 `enabled` 屬性設定為 `true` 。 這項設定會套用 processwide 並影響所有方法。  
  
 -或-  
  
- 將 <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> 屬性套用至包含例外狀況區塊的方法 `catch` 。  
  
 只有 .NET Framework 4 和更新版本才提供此設定元素。  
  
## <a name="example"></a>範例  

 下列範例示範如何指定應用程式應該在 .NET Framework 4 之前還原為行為，並攔截所有損毀狀態例外狀況失敗。  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [執行階段設定結構描述](index.md)
- [設定檔架構](../index.md)
