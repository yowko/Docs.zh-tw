---
title: C# 保留屬性:全域屬性
ms.date: 04/09/2020
description: 屬性提供編譯器用於理解程式更多語意的中繼資料
ms.openlocfilehash: f855f32cd7349da34ffbd20fededdf42c3023938
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389853"
---
# <a name="reserved-attributes-assembly-level-attributes"></a>保留屬性:程式集等級屬性

大部分屬性會套用至特定語言項目 (例如類別或方法)；不過，有些屬性是全域屬性，其套用至整個組件或模組。 例如，<xref:System.Reflection.AssemblyVersionAttribute> 屬性可以用來將版本資訊內嵌到組件，與下面類似：

```csharp
[assembly: AssemblyVersion("1.0.0.0")]
```

全域屬性出現在任何頂級`using`指令之後的原始碼中,並在任何類型、模組或命名空間聲明之前顯示。 全域屬性可以出現在多個原始程式檔中，但必須使用單一編譯階段編譯檔案。 Visual Studio 將全域屬性添加到 .NET Framework 專案中的AssemblyInfo.cs檔中。 這些屬性不會添加到 .NET Core 專案中。

組件屬性是提供組件相關資訊的值。 它們的分類如下：

- 組件識別屬性
- 資訊屬性
- 組件資訊清單屬性

## <a name="assembly-identity-attributes"></a>組件識別屬性

三個具有強式名稱 (如果適用) 的屬性會判斷組件的識別：名稱、版本與文化特性。 這些屬性會形成組件的完整名稱，且在程式碼中參考組件時需要用到。 您可以使用屬性來設定組件的版本和文化特性。 但是,名稱值由編譯器、[程式集資訊對話框](/visualstudio/ide/reference/assembly-information-dialog-box)中的 Visual Studio IDE 或創建程式集時的程式集連結器 (Al.exe) 設置。 程式集名稱基於程式集清單。 <xref:System.Reflection.AssemblyFlagsAttribute> 屬性指定組件的多個複本是否可以並存。

下表顯示識別屬性。

|屬性|目的|
|---------------|-------------|
|<xref:System.Reflection.AssemblyVersionAttribute>|指定組件的版本。|
|<xref:System.Reflection.AssemblyCultureAttribute>|指定組件所支援的文化特性。|
|<xref:System.Reflection.AssemblyFlagsAttribute>|指定是否支援在相同電腦上、相同處理程序中或相同應用程式定義域中並存執行組件。|

## <a name="informational-attributes"></a>資訊屬性

您可以使用資訊屬性為程式集提供其他公司或產品資訊。 下表顯示 <xref:System.Reflection?displayProperty=nameWithType> 命名空間中定義的資訊屬性。

|屬性|目的|
|---------------|-------------|
|<xref:System.Reflection.AssemblyProductAttribute>|指定程式集清單的產品名稱。|
|<xref:System.Reflection.AssemblyTrademarkAttribute>|指定程式集清單的商標。|
|<xref:System.Reflection.AssemblyInformationalVersionAttribute>|指定程式集清單的資訊版本。|
|<xref:System.Reflection.AssemblyCompanyAttribute>|指定程式集清單的公司名稱。|
|<xref:System.Reflection.AssemblyCopyrightAttribute>|定義自訂屬性，以指定組件資訊清單的版權。|
|<xref:System.Reflection.AssemblyFileVersionAttribute>|為 Win32 檔版本資源設置特定的版本號。|
|<xref:System.CLSCompliantAttribute>|表示組件是否符合 Common Language Specification (CLS) 規範。|

## <a name="assembly-manifest-attributes"></a>組件資訊清單屬性

您可以使用組件資訊清單屬性，在組件資訊清單中提供資訊。 這些屬性包括標題、說明、預設別名和配置。 下表顯示 <xref:System.Reflection?displayProperty=nameWithType> 命名空間中定義的資訊清單屬性。

|屬性|目的|
|---------------|-------------|
|<xref:System.Reflection.AssemblyTitleAttribute>|指定程式集清單的程式集標題。|
|<xref:System.Reflection.AssemblyDescriptionAttribute>|指定程式集清單的程式集說明。|
|<xref:System.Reflection.AssemblyConfigurationAttribute>|為程式集清單指定程式集配置(如零售或調試)。|
|<xref:System.Reflection.AssemblyDefaultAliasAttribute>|定義組件資訊清單的易記預設別名。|
