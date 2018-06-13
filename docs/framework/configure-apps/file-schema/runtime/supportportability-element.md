---
title: '&lt;supportPortability&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0a8a454919a195a0f0c03ed6890e51b2723f64fb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754102"
---
# <a name="ltsupportportabilitygt-element"></a>&lt;supportPortability&gt;項目
指定應用程式可以在兩個不同的 .NET Framework 實作中參考相同的組件，方法是停用將組件視為同等的預設行為 (此預設行為是基於應用程式可攜性的考量)。  
  
 \<設定 > 項目  
\<runtime > 項目  
\<assemblyBinding > 項目  
\<supportPortability > 項目  
  
## <a name="syntax"></a>語法  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|PKT|必要屬性。<br /><br /> 字串形式指定受影響的組件公開金鑰語彙基元。|  
|enabled|選擇性屬性。<br /><br /> 指定是否應該啟用指定的.NET Framework 組件實作之間的可攜性的支援。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|描述|  
|-----------|-----------------|  
|true|啟用支援不同的實作指定的.NET Framework 組件的可攜性。 這是預設值。|  
|False|停用指定的.NET Framework 組件實作之間的可攜性的支援。 這可讓應用程式具備多個指定的組件實作的參考。|  
  
### <a name="child-elements"></a>子項目  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
  
## <a name="remarks"></a>備註  
 開頭為[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]，支援自動提供的應用程式可以使用其中一個的.NET Framework 中，兩個實作，例如.NET Framework 實作或.NET Framework for Silverlight 實作。 組件繫結器會將兩個實作特定的.NET Framework 組件視為對等項目。 在少數情況下，此應用程式可攜性功能會造成問題。 在這些情況下，`<supportPortability>`項目可以用來停用此功能。  
  
 這類案例之一是具有參考.NET Framework 實作和.NET Framework for Silverlight 實作的特定參考組件的組件。 例如，寫入 Windows Presentation Foundation (WPF) XAML 設計工具可能需要參考兩個 WPF 桌面實作中，在設計工具使用者介面，和包含 Silverlight 實作中的 WPF 子集。 根據預設，不同的參考會導致編譯器錯誤，因為組件繫結關係會將兩個組件視為對等項目。 這個項目停用預設的行為，並可讓編譯成功。  
  
> [!IMPORTANT]
>  為了讓編譯器將資訊傳遞至 common language runtime 的組件繫結邏輯，您必須使用`/appconfig`編譯器選項以指定 app.config 檔案，其中包含這個元素的位置。  
  
## <a name="example"></a>範例  
 下列範例會啟用應用程式的.NET Framework 實作和.NET Framework for Silverlight 實作這兩個實作中有任何.NET Framework 組件的參考。 `/appconfig`編譯器選項必須用來指定此 app.config 檔案的位置。  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding>  
         <supportPortability PKT="7cec85d7bea7798e" enable="false"/>  
         <supportPortability PKT="31bf3856ad364e35" enable="false"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱  
 [/appconfig （C# 編譯器選項）](http://msdn.microsoft.com/library/ee523958.aspx)  
 [.NET framework 組件統一概觀](http://msdn.microsoft.com/library/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)
