---
title: 設定元件屬性
ms.date: 08/20/2019
helpviewer_keywords:
- assemblies [.NET Framework], attributes
- assembly binding, attributes
- assembly manifest, attributes
ms.assetid: 36a98a81-b5b5-4c19-912a-11f91eff7f4e
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: d0809ec3da5a12abe950e63f9665037323a0ab39
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991672"
---
# <a name="set-assembly-attributes"></a>設定元件屬性

組件屬性是提供組件相關資訊的值。 屬性可分成下列幾組資訊：

- 組件識別屬性

- 資訊屬性

- 組件資訊清單屬性

- 強式名稱屬性

## <a name="assembly-identity-attributes"></a>組件識別屬性

三個屬性連同強式名稱 (如果適用) 會判斷組件的識別：名稱、版本與文化特性。 這些屬性會形成組件的完整名稱，且在參考程式碼中的組件時會需要用到。 您可以使用屬性來設定組件的版本和文化特性。 編譯器或 [組件連結器 (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) 會在建立組件時，以包含組件資訊清單的檔案為基礎來設定名稱值。

下表說明版本與文化特性屬性。

|組件識別屬性|描述|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyCultureAttribute>|列舉的欄位，會指出組件所支援的文化特性。 組件也可以指定文化特性獨立性，表示其包含預設文化特性的資源。 **注意：** 執行階段會將任何未將文化特性屬性設為 null 的組件作為附屬組件。 這類組件會受限於附屬組件繫結規則。 如需詳細資訊，請參閱[執行時間如何找出元件](../../framework/deployment/how-the-runtime-locates-assemblies.md)。|
|<xref:System.Reflection.AssemblyFlagsAttribute>|此值用以設定組件屬性，例如組件是否可並存執行。|
|<xref:System.Reflection.AssemblyVersionAttribute>|格式為 *major*.*minor*.*build*.*revision* 的數值 (例如 2.4.0.0)。 通用語言執行平台會使用此值來執行強式名稱組件中的繫結作業。 **注意：** 如果 <xref:System.Reflection.AssemblyInformationalVersionAttribute> 屬性未套用到組件，則 <xref:System.Reflection.AssemblyVersionAttribute> 屬性所指定的版本號碼會由 <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType>、<xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType>與 <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> 屬性所使用。|

下列程式碼範例顯示如何將版本與文化特性屬性套用至組件。

```cpp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")];
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")];
```

```csharp
// Set version number for the assembly.
[assembly:AssemblyVersionAttribute("4.3.2.1")]
// Set culture as German.
[assembly:AssemblyCultureAttribute("de")]
```

```vb
' Set version number for the assembly.
<Assembly:AssemblyVersionAttribute("4.3.2.1")>
' Set culture as German.
<Assembly:AssemblyCultureAttribute("de")>
```

## <a name="informational-attributes"></a>資訊屬性

您可以使用資訊屬性，以提供組件其他的公司或產品資訊。 下表說明可套用至組件的資訊屬性。

|資訊屬性|描述|
|-----------------------------|-----------------|
|<xref:System.Reflection.AssemblyCompanyAttribute>|此字串值指定公司名稱。|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|此字串值指定著作權資訊。|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|此字串值指定 Win32 檔案版本號碼。 這通常會預設為組件版本。|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|此字串值指定的版本資訊不為通用語言執行平台所用，例如完整的產品版本號碼。 **注意：** 如果這個屬性會套用至組件，則其所指定的字串可以在執行階段透過使用 <xref:System.Windows.Forms.Application.ProductVersion%2A?displayProperty=nameWithType> 屬性加以取得。 字串也會在 <xref:System.Windows.Forms.Application.UserAppDataPath%2A?displayProperty=nameWithType> 與 <xref:System.Windows.Forms.Application.UserAppDataRegistry%2A?displayProperty=nameWithType> 屬性所提供的路徑及登錄機碼中使用。|
|<xref:System.Reflection.AssemblyProductAttribute>|此字串值指定產品資訊。|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|此字串值指定商標資訊。|

這些屬性可以出現在組件的 Windows 內容頁面上，或可以使用 **/win32res** 編譯器選項加以覆寫，以指定您自己的 Win32 資源檔。

## <a name="assembly-manifest-attributes"></a>組件資訊清單屬性

您可以使用組件資訊清單屬性，在組件資訊清單中提供資訊，包括標題、描述、預設別名以及設定。 下表說明組件資訊清單屬性。

|組件資訊清單屬性|描述|
|---------------------------------|-----------------|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|此字串值表示組件的設定，例如 Retail 或 Debug。 執行階段不使用此值。|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|此字串值指定可供參考組件使用的預設別名。 此值會在組件本身的名稱不容易記時 (例如 GUID 值) 提供易記名稱。 也可以使用此值作為完整組件名稱的簡短形式。|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|此字串值指定簡短描述，該描述彙總組件的本質與用途。|
|<xref:System.Reflection.AssemblyTitleAttribute>|此字串值指定組件的易記名稱。 例如，名為*comdlg*的元件可能會有「Microsoft 通用對話方塊控制項」標題。|

## <a name="strong-name-attributes"></a>強式名稱屬性

您可以使用強式名稱屬性來設定組件的強式名稱。 下表說明強式名稱屬性。

|強式名稱屬性|描述|
|----------------------------|-----------------|
|<xref:System.Reflection.AssemblyDelaySignAttribute>|此布林值表示正在使用延遲簽章。|
|<xref:System.Reflection.AssemblyKeyFileAttribute>|此字串值表示檔案名稱，該檔案包含公開金鑰 (如果使用延遲簽章) 或公開與私密金鑰，而金鑰以參數形式傳遞至該屬性的建構函式。 請注意，檔案名是相對於輸出檔案路徑（ *.exe*或 *.dll*），而不是來源檔案路徑。|
|<xref:System.Reflection.AssemblyKeyNameAttribute>|表示內含金鑰組的金鑰容器，而該金鑰組以參數形式傳遞至該屬性的建構函式。|

下列程式碼範例顯示使用延遲簽署來建立強式名稱元件時所要套用的屬性，其具有名為*myKey*的公開金鑰檔案。

```cpp
[assembly:AssemblyKeyFileAttribute("myKey.snk")];
[assembly:AssemblyDelaySignAttribute(true)];
```

```csharp
[assembly:AssemblyKeyFileAttribute("myKey.snk")]
[assembly:AssemblyDelaySignAttribute(true)]
```

```vb
<Assembly:AssemblyKeyFileAttribute("myKey.snk")>
<Assembly:AssemblyDelaySignAttribute(True)>
```

## <a name="see-also"></a>另請參閱

- [建立元件](create.md)
- [具有元件的程式](program.md)
