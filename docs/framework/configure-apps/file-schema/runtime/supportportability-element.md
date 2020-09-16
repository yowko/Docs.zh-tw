---
title: <supportPortability> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- supportPortability element
- <supportPortability> element
ms.assetid: 6453ef66-19b4-41f3-b712-52d0c2abc9ca
ms.openlocfilehash: 99fa51238040f21d998a8c6c2aef7c13d288104a
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551581"
---
# <a name="supportportability-element"></a>\<supportPortability> 項目
指定應用程式可以在兩個不同的 .NET Framework 實作中參考相同的組件，方法是停用將組件視為同等的預設行為 (此預設行為是基於應用程式可攜性的考量)。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<supportPortability>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<supportPortability PKT="public_key_token" enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|說明|  
|---------------|-----------------|  
|PKT|必要屬性。<br /><br /> 以字串形式指定受影響元件的公開金鑰 token。|  
|已啟用|選擇性屬性。<br /><br /> 指定是否應啟用指定 .NET Framework 元件之實執行之間的可攜性支援。|  
  
## <a name="enabled-attribute"></a>啟用屬性  
  
|值|說明|  
|-----------|-----------------|  
|true|啟用指定 .NET Framework 元件之實執行之間的可攜性支援。 此為預設值。|  
|false|停用指定之 .NET Framework 元件之執行之間的可攜性支援。 這可讓應用程式參考指定元件的多個執行。|  
  
### <a name="child-elements"></a>子元素  

無。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
|`assemblyBinding`|包含有關組件版本重新導向和組件位置的資訊。|  
  
## <a name="remarks"></a>備註  

從 .NET Framework 4 開始，系統會自動為可使用兩個 .NET Framework 執行之一的應用程式（例如 .NET Framework 的執行或 Silverlight 執行的 .NET Framework）提供支援。 特定 .NET Framework 元件的兩個實作為元件系結器的相等專案。 在幾個案例中，此應用程式可攜性功能會造成問題。 在這些情況下， `<supportPortability>` 元素可以用來停用功能。  
  
其中一個這類案例是必須同時參考 .NET Framework 的執行和 .NET Framework 的元件，以進行特定參考元件的 Silverlight 執行。 例如，以 Windows Presentation Foundation (WPF) 撰寫的 XAML 設計工具可能需要參考 WPF 桌面執行、設計工具的使用者介面，以及包含在 Silverlight 執行中的 WPF 子集。 根據預設，不同的參考會導致編譯器錯誤，因為組件繫結關係會將兩個組件視為對等項目。 這個元素會停用預設行為，並允許編譯成功。  
  
> [!IMPORTANT]
> 為了讓編譯器將資訊傳遞給 common language runtime 的元件系結邏輯，您必須使用 `/appconfig` 編譯器選項來指定包含此專案之 app.config 檔案的位置。  
  
## <a name="example"></a>範例  

下列範例可讓應用程式同時參考同時存在於兩個執行中的任何 .NET Framework 元件的 .NET Framework 執行和 .NET Framework。 `/appconfig`編譯器選項必須用來指定此 app.config 檔的位置。  
  
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

- [-appconfig (C# 編譯器選項)](../../../../csharp/language-reference/compiler-options/appconfig-compiler-option.md)
- [.NET Framework 組件對應轉換概觀](/previous-versions/dotnet/netframework-4.0/db7849ey(v=vs.100))
