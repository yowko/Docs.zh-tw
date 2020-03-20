---
title: <compilers> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#compilers
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.codedom/compilers
helpviewer_keywords:
- compiler configuration elements, <compilers> element
- <compilers> element
- compilers element
ms.assetid: d40fba59-98f9-4783-ae0c-2ebea27ce77b
ms.openlocfilehash: 09b1efe321c39402c9280eda0e9def9112462470
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155410"
---
# <a name="compilers-element"></a>\<編譯器>元素
用於編譯器配置元素的容器;包含零個或多個[\<編譯器>](compiler-element.md)元素。  

[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統.代碼>**](system-codedom-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<編譯器>**

## <a name="syntax"></a>語法  
  
```xml  
<compilers>  
  <compiler ... />  
</compilers>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<編譯器>元素](compiler-element.md)|指定語言提供者的編譯器組態屬性。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<配置>元素](../configuration-element.md)|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|[\<系統.代碼>元素](system-codedom-element.md)|指定可用語言提供者的編譯器組態設定。|  
  
## <a name="remarks"></a>備註  
 [ \<>元素的編譯器](compilers-element.md)包含電腦上的語言提供程式的編譯器配置設置。 每個[\<編譯器>](compiler-element.md)元素指定特定語言提供程式的編譯器配置屬性。  
  
 .NET 框架定義電腦設定檔 （Machine.config） 中的初始編譯器和語言提供程式設置。 開發人員和編譯器廠商可以為新的 <xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=nameWithType> 實作新增組態設定。 使用 <xref:System.CodeDom.Compiler.CodeDomProvider.GetAllCompilerInfo%2A?displayProperty=nameWithType> 方法，以程式設計方式列舉電腦上的語言提供者和編譯器組態設定。  
  
## <a name="configuration-file"></a>組態檔  
 此元素可用於電腦設定檔和應用程式佈建檔。  
  
## <a name="example"></a>範例  
 下列範例說明典型的編譯器組態項目。  
  
```xml  
<configuration>  
   <system.codedom>  
     <compilers>  
       <!-- zero or more compiler elements -->  
       <compiler
          language="c#;cs;csharp"
          extension=".cs"  
          type="Microsoft.CSharp.CSharpCodeProvider, System, Version=1.0.5000.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
          compilerOptions=""
          warningLevel="1" />  
     </compilers>  
   </system.codedom>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.CodeDom.Compiler.CompilerInfo>
- <xref:System.CodeDom.Compiler.CodeDomProvider>
- [組態檔結構描述](../index.md)
- [編譯器和語言提供程式設置架構](index.md)
- [\<編譯器>元素](compiler-element.md)
