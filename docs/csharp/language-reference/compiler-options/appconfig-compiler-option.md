---
title: "-appconfig (C# 編譯器選項)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /appconfig
helpviewer_keywords:
- /appconfig compiler option [C#]
- -appconfig compiler option [C#]
- appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: a3f2c1bc9d0d3fec0635d284f64138f0432f59ef
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="-appconfig-c-compiler-options"></a>-appconfig (C# 編譯器選項)
**-appconfig** 編譯器選項可讓 C# 應用程式將組件應用程式組態檔 (app.config) 的位置指定到組件繫結時間的通用語言執行平台 (CLR)。  
  
## <a name="syntax"></a>語法  
  
```console  
-appconfig:file  
```  
  
## <a name="arguments"></a>引數  
 `file`  
 必要。 包含組件繫結設定的應用程式組態檔。  
  
## <a name="remarks"></a>備註  
 **-appconfig** 的其中一種用法就是進階案例；在此案例中，組件必須同時參考特定參考組件的 .NET Framework 版本以及 .NET Framework for Silverlight 版本。 例如，以 Windows Presentation Foundation (WPF) 撰寫的 XAML 設計工具，可能必須同時參考 WPF Desktop (設計工具的使用者介面) 和 Silverlight 所附的 WPF 子集。 相同的設計工具組件必須存取這兩個組件。 根據預設，不同的參考會導致編譯器錯誤，因為組件繫結關係會將兩個組件視為對等項目。  
  
 **-appconfig** 編譯器選項可讓您使用 `<supportPortability>` 標記指定停用預設行為的 app.config 檔案位置，如下列範例所示。  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 編譯器會將檔案位置傳遞至 CLR 的組件繫結關係邏輯。  
  
> [!NOTE]
>  如果使用 Microsoft Build Engine (MSBuild) 來建置應用程式，您可以將屬性標記新增至 .csproj 檔案，以設定 **-appconfig** 編譯器選項。 若要使用專案中已設定的 app.config 檔案，請將屬性標記 `<UseAppConfigForCompiler>` 新增至 .csproj 檔案，並將其值設定為 `true`。 若要指定不同的 app.config 檔案，請新增屬性標記 `<AppConfigForCompiler>` 並將其值設定為檔案位置。  
  
## <a name="example"></a>範例  
 下例示範的 app.config 檔案，可讓應用程式同時參考存在於兩個實作中之任何 .NET Framework 組件的 .NET Framework 實作和 .NET Framework for Silverlight 實作。 **-appconfig** 編譯器選項會指定此 app.config 檔案的位置。  
  
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
  
## <a name="see-also"></a>請參閱  
 [\<supportPortability> 項目](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)  
 [依字母順序列出 C# 編譯器選項](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)
