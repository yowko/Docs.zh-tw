---
title: <shadowCopyVerifyByTimestamp> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: c0dc190e69ca9650d518ee297b12f79f8c47d58b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183971"
---
# <a name="shadowcopyverifybytimestamp-element"></a>\<shadowCopyVerifyByTimestamp> 項目

指定陰影複製是否使用 .NET Framework 4 中引進的預設啟動行為，或還原為舊版 .NET Framework 的啟動行為。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|已啟用|必要屬性。<br /><br /> 指定在啟動時，使用陰影複製的應用程式域是否會比較元件時間戳記，以判斷元件是否已在陰影複製元件之前更新。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|true|在啟動時，只會複製自上次複製到陰影複製目錄以來已更新的元件。 這是 .NET Framework 4 的預設值。|  
|false|還原為舊版 .NET Framework 的啟動行為，也就是在啟動時複製所有檔案。|  
  
### <a name="child-elements"></a>子元素  

 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## <a name="remarks"></a>備註  

 從 .NET Framework 4 開始，只有當元件的時間戳記表示自上次複製到陰影複製目錄以來已變更時，才會陰影複製元件。 這可改善使用陰影複製的許多應用程式的啟動時間，如 [陰影複製元件](../../../app-domains/shadow-copy-assemblies.md)中所述。 組件更新比例與頻率相當高的應用程式可能不會受益於這種行為變更。 在這種情況下，您可以使用此項目還原舊版 .NET Framework 的行為。  
  
## <a name="example"></a>範例  

 下列範例顯示如何在 .NET Framework 4 中停用陰影複製的預設啟動行為，並還原為舊版 .NET Framework 的啟動行為。  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [設定檔架構](../index.md)
- [陰影複製組件](../../../app-domains/shadow-copy-assemblies.md)
