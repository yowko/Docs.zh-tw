---
title: -langversion (C# 編譯器選項)
ms.date: 08/23/2019
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 81cf336f94815dd3f2c88995eb34ae03b8220097
ms.sourcegitcommit: dfd612ba454ce775a766bcc6fe93bc1d43dfda47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/09/2019
ms.locfileid: "72179925"
---
# <a name="-langversion-c-compiler-options"></a>-langversion (C# 編譯器選項)

讓編譯器只接受所選擇 C# 語言規格中所含的語法。

## <a name="syntax"></a>語法

```console
-langversion:option
```

## <a name="arguments"></a>引數

 `option`  
 下列是有效值：

|選項|意義|
|------------|-------------|
|preview|編譯器會接受它可支援之最新預覽版本的所有有效語言語法。|
|latest|編譯器會接受它可支援之最新版本 (包括次要版本) 的所有有效語言語法。|
|latestMajor|編譯器會接受它可支援之最新主要版本的所有有效語言語法。|
|8.0|編譯器只會接受 C# 8.0 或更低版本中所含的語法。|
|7.3|編譯器只會接受 C# 7.3 或更低版本中所含的語法。|
|7.2|編譯器只會接受 C# 7.2 或更低版本中所含的語法。|
|7.1|編譯器只會接受 C# 7.1 或更低版本中所含的語法。|
|7|編譯器只會接受 C# 7.0 或更低版本中所含的語法。|
|6|編譯器只會接受 C# 6.0 或更低版本中所含的語法。|
|5|編譯器只會接受 C# 5.0 或更低版本中所含的語法。|
|4|編譯器只會接受 C# 4.0 或更低版本中所含的語法。|
|3|編譯器只會接受 C# 3.0 或更低版本中所含的語法。|
|ISO-2|編譯器只會接受 ISO/IEC 23270:2006 C# （2.0）中所包含的語法。|
|ISO-1|編譯器只會接受 ISO/IEC 23270:2003 C# （1.0/1.2）中所包含的語法。|

預設語言版本取決於您應用程式的目標 Framework，以及安裝的 SDK 或 Visual Studio 版本。 這些規則定義于設定[語言版本](../configure-language-version.md#defaults)一文。

## <a name="remarks"></a>備註

C# 應用程式所參考的中繼資料不限於 **-langversion** 編譯器選項。
  
因為每個版本的 C# 編譯器都包含語言規格的延伸模組，所以 **-langversion** 不會提供舊版編譯器的相等功能。

此外，雖然 C# 版本更新通常會與主要 .NET Framework 版本一致，但是新語法和功能不需要繫結至該特定架構版本。 雖然新功能一定需要也要與 C# 修訂一起發行的新編譯器更新，但是每個特定功能都有自己的最低 .NET API 或通用語言執行平台需求，可讓它包含 NuGet 套件或其他程式庫以在舊版架構上執行。

不論使用的 **-langversion** 設定為何，您都會使用目前版本的通用語言執行平台來建立 .exe 或 .dll。 其中一個例外狀況是 Friend 組件和 [-moduleassemblyname (C# 編譯器選項)](./moduleassemblyname-compiler-option.md)，這些都是在 **-langversion:ISO-1** 下運作。  

如需指定C#語言版本的其他方式，請參閱[ C#選取語言版本](../configure-language-version.md)一文。

如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>。

## <a name="c-language-specification"></a>C# 語言規格

|Version|連結|描述|
|-------|----|-----------|
|C# 7.0 與更新版本||目前無法使用|
|C# 6.0|[連結](../language-specification/index.md)|C# 語言規格版本 6 - 非官方草稿：.NET Foundation|
|C# 5.0|[下載 PDF](https://www.ecma-international.org/publications/files/ECMA-ST/ECMA-334.pdf)|標準 ECMA-334 第 5 版|
|C# 3.0|[下載 DOC](https://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C# 語言規格 3.0 版：Microsoft Corporation|
|C# 2.0|[下載 PDF](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%204th%20edition%20June%202006.pdf)|標準 ECMA-334 第 4 版|
|C# 1.2|[下載 DOC](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%202nd%20edition%20December%202002.pdf)|C# 語言規格 1.2 版：Microsoft Corporation|
|C# 1.0|[下載 DOC](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/ECMA-334%201st%20edition%20December%202001.pdf)|C# 語言規格 1.0 版：Microsoft Corporation|

## <a name="minimum-sdk-version-needed-to-support-all-language-features"></a>支援所有語言功能所需的最低 SDK 版本

下表列出具有支援對應語言版本之C#編譯器的 SDK 的最低版本：

|C#版本|最低 SDK 版本|
|----------|-------------------|
|C# 8.0| Microsoft Visual Studio/Build Tools 2019、16.3 版或 .NET Core 3.0 SDK |
|C# 7.3| Microsoft Visual Studio/Build Tools 2017 15.7 版 |
|C# 7.2| Microsoft Visual Studio/Build Tools 2017 15.5 版 |
|C# 7.1| Microsoft Visual Studio/Build Tools 2017 15.3 版 |
|C# 7.0| Microsoft Visual Studio/Build Tools 2017 |
|C# 6| Microsoft Visual Studio/Build Tools 2015 |
|C#第| Microsoft Visual Studio/Build Tools 2012 或配套的 .NET Framework 4.5 編譯器 |
|C# 4| Microsoft Visual Studio/Build Tools 2010 或配套的 .NET Framework 4.0 編譯器 |
|C#第| Microsoft Visual Studio/Build Tools 2008 或配套的 .NET Framework 3.5 編譯器 |
|C#2| Microsoft Visual Studio/Build Tools 2005 或配套的 .NET Framework 2.0 編譯器 |
|C#1.0/1。2 | Microsoft Visual Studio/Build Tools .NET 2002 或配套的 .NET Framework 1.0 編譯器 |

## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
