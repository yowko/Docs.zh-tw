---
title: ControlBuilderInterceptor 類別
ms.date: 08/11/2020
api_name:
- System.Web.Compilation.ControlBuilderInterceptor
api_location:
- System.Web.dll
api_type:
- Assembly
topic_type:
- apiref
ms.openlocfilehash: 312d977f832d262b1bebc6638280b67b133babdf
ms.sourcegitcommit: 70d6a7e4f7187cbfa332f0f8be76566f7828cfcd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88084392"
---
# <a name="controlbuilderinterceptor-class"></a>ControlBuilderInterceptor 類別

`ControlBuilderInterceptor`類別可讓您自訂或控制編譯進程。

## <a name="syntax"></a>語法

```csharp
internal class ControlBuilderInterceptor
```

> [!WARNING]
> `ControlBuilderInterceptor`類別是內部的，不適合直接在程式碼中使用。
>
> 如「備註」一節所述，您可以檢查此類型是否存在，以判斷是否有攔截器類型支援。 在任何情況下，Microsoft 不支援在實際執行應用程式中使用此類別。

## <a name="remarks"></a>備註

在 .NET Framework 2.0 和 .NET Framework 3.5 中， [8 月 2020](https://portal.msrc.microsoft.com/security-guidance/releasenotedetail/2020-Aug)更新新增了使用攔截器類型來自訂或控制編譯器的支援。 <xref:System.Type.GetType?displayProperty=nameWithType>如下列程式碼所示，您可以使用來檢查此支援是否存在，以判斷該類型是否存在 `ControlBuilderInterceptor` 。

```csharp
Type type = Type.GetType("System.Web.Compilation.ControlBuilderInterceptor, System.Web, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a");
```

如果傳回值為非 null，則會有攔截器支援。 如果傳回值為 `null` ，或擲回例外狀況，則不會安裝2020年8月的更新，而且不會有攔截器支援。

如果有攔截器支援，您可以撰寫並註冊與編譯器互動的攔截器型別，其方式與更新版本 .NET Framework 的方法完全相同 <xref:System.Web.Compilation.ControlBuilderInterceptor> 。 在 .NET Framework 2.0 和 .NET Framework 3.5 中，攔截器類型可以是符合下列需求的任何類別：

* 具有公用的無參數的函式。
* 具有名為的公用、非靜態方法， `PreControlBuilderInit` `OnProcessGeneratedCode` 其具有與和方法相同的簽章和語義 <xref:System.Web.Compilation.ControlBuilderInterceptor.PreControlBuilderInit(System.Web.UI.ControlBuilder,System.Web.UI.TemplateParser,System.Web.UI.ControlBuilder,System.Type,System.String,System.String,System.Collections.IDictionary,System.Collections.IDictionary)> <xref:System.Web.Compilation.ControlBuilderInterceptor.OnProcessGeneratedCode(System.Web.UI.ControlBuilder,System.CodeDom.CodeCompileUnit,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeTypeDeclaration,System.CodeDom.CodeMemberMethod,System.CodeDom.CodeMemberMethod,System.Collections.IDictionary)> ，後者存在於較新的 .NET Framework 版本中。

使用 `aspnet:20ControlBuilderInterceptor` ASP.NET 應用程式設定 () 中的金鑰，註冊攔截器類型 `<appSettings>` 。 此應用程式設定必須列在您的電腦或應用程式*web.config*檔中。 使用元件限定的型別名稱來指定攔截器型別。 下列範例顯示如何註冊名為的攔截器型別 `Fabrikam.Interceptor` 。

```xml
<configuration>
  ...
  <appSettings>
    ...
    <add key="aspnet:20ControlBuilderInterceptor"
         value="Fabrikam.Interceptor, Fabrikam, Version=1.0.0.0, Culture=neutral, PublicKeyToken=2b3831f2f2b744f7" />
  </appSettings>
</configuration>

To retrieve the assembly-qualified name of a type, use the <xref:System.Type.AssemblyQualifiedName?displayProperty=nameWithType> property, as demonstrated in the following code.

```csharp
string assemblyQualifiedName = typeof(Fabrikam.Interceptor).AssemblyQualifiedName;
```

當攔截器支援存在時，編譯器會以上述方式與列出的類型互動。 當攔截器支援不存在時，會忽略應用程式設定，而且不會有任何作用。

## <a name="requirements"></a>規格需求

**命名空間：** System.web. 編譯

**元件：** System.Web.dll) 中的 system.web (

**.NET Framework 版本：** 3.5、2。0
