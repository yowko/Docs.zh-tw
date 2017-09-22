---
title: "-appconfig (C# 編譯器選項)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /appconfig
dev_langs:
- CSharp
helpviewer_keywords:
- /appconfig compiler option [C#]
ms.assetid: 1cdbcbcc-7813-4010-b5b8-e67c107c5a98
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2aede966f92af3c94f4591b68732dbdbf5a4c5c9
ms.contentlocale: zh-tw
ms.lasthandoff: 09/19/2017

---
# /appconfig (C# Compiler Options)
**\/appconfig** 編譯器選項可讓 C\# 應用程式在組件繫結階段將組件的應用程式組態 \(app.config\) 檔案位置指定至 Common Language Runtime \(CLR\)。  
  
## 語法  
  
```  
/appconfig:file  
```  
  
## Arguments  
 `file`  
 必要項。  應用程式組態檔包含組件繫結設定。  
  
## 備註  
 **\/appconfig** 的用法之一就是進階案例，在此案例中組件必須同時參考特定參考組件的 .NET Framework 版本以及 Silverlight 版的 .NET Framework 版本。  例如，以 Windows Presentation Foundation \(WPF\) 撰寫的 XAML 設計工具可能需要參考 WPF 桌面 \(適合設計人員的使用者介面\) 與 Silverlight 隨附的 WPF 的子集。  相同的設計工具組件必須存取這兩個組件。  預設情況下，不同的參考會造成編譯器錯誤，因為組件繫結會將兩個組件視為相等。  
  
 **\/appconfig** 編譯器選項可讓您使用 `<supportPortability>` 標記來指定會停用預設行為的 app.config 檔案位置，如下例所示。  
  
 `<supportPortability PKT="7cec85d7bea7798e" enable="false"/>`  
  
 編譯器會將檔案的位置傳遞到 CLR 的組件繫結邏輯。  
  
> [!NOTE]
>  如果您使用 Microsoft Build Engine \(MSBuild）組建應用程式，可以透過將屬性標記新增至 .csproj 檔案來設定  **\/appconfig**編譯器選項。  若要使用專案中已設定的 app.config 檔，請將屬性標記`<UseAppConfigForCompiler>` 加入至 .csproj 檔，並將其值設定為 `true`。  若要指定不同的 app.config 檔，請加入屬性標記`<AppConfigForCompiler>`，並將其值設定為檔案的位置。  
  
## 範例  
 下列範例示範 app.config 檔案，該檔案讓應用程式能夠參考 .NET Framework 實作，和存在於兩個實作中任何 .NET Framework 組件其 Silverlight 實作的 .NET Framework。  **\/appconfig** 編譯器選項可指定這個 app.config 檔案的位置。  
  
```  
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
 [.NET Framework 組件對應轉換概觀](http://msdn.microsoft.com/en-us/8d8cc65e-031d-463b-bde3-2c6dc2e3bc48)   
 [\<supportPortability> 項目](../../../framework/configure-apps/file-schema/runtime/supportportability-element.md)   
 [依字母順序列出 C# 編譯器選項](../../../csharp/language-reference/compiler-options/listed-alphabetically.md)

