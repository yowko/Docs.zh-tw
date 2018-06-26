---
title: -langversion (C# 編譯器選項)
ms.date: 05/14/2018
f1_keywords:
- /langversion
helpviewer_keywords:
- /langversion compiler option [C#]
- -langversion compiler option [C#]
- langversion compiler option [C#]
ms.assetid: 3fb00b05-a0ff-4782-b313-13a4c0f62d94
ms.openlocfilehash: 2a9501c883fec7478932b22ea2cdcad70865e0fd
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696282"
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
|default|編譯器會接受它可支援之最新主要版本的所有有效語言語法。|
|ISO-1|編譯器只會接受 ISO/IEC 23270:2003 C# (1.0/1.2) <sup id="TISO1">[ISO1](#FISO1)</sup> 中所含的語法|  
|ISO-2|編譯器只會接受 ISO/IEC 23270:2006 C# (2.0) <sup id="TISO2">[ISO2](#FISO2)</sup> 中所含的語法。|
|3|編譯器只會接受 C# 3.0 或較低 <sup id="TCS3">[CS3](#FCS3)</sup> 中所含的語法。|
|4|編譯器只會接受 C# 4.0 或較低 <sup id="TCS4">[CS4](#FCS4)</sup> 中所含的語法。|
|5|編譯器只會接受 C# 5.0 或較低 <sup id="TCS5">[CS5](#FCS5)</sup> 中所含的語法。|
|6|編譯器只會接受 C# 6.0 或較低 <sup id="TCS6">[CS6](#FCS6)</sup> 中所含的語法。|
|7|編譯器只會接受 C# 7.0 或較低 <sup id="TCS7">[CS7](#FCS7)</sup> 中所含的語法。|
|7.1|編譯器只會接受 C# 7.1 或較低 <sup id="TCS71">[CS71](#FCS71)</sup> 中所含的語法|
|7.2|編譯器只會接受 C# 7.2 或較低 <sup id="TCS72">[CS72](#FCS72)</sup> 中所含的語法|
|7.3|編譯器只會接受 C# 7.3 或較低 <sup id="TCS73">[CS73](#FCS73)</sup> 中所含的語法|
|latest|編譯器會接受它可支援的所有有效語言語法。|

<!--- Uncomment and move these above
|8|The compiler accepts only syntax that is included in C# 8 or lower <sup id="TCS8">[CS8](#FCS8)</sup>|
-->

  
## <a name="remarks"></a>備註  
 C# 應用程式所參考的中繼資料不限於 **-langversion** 編譯器選項。  
  
 因為每個版本的 C# 編譯器都包含語言規格的延伸模組，所以 **-langversion** 不會提供舊版編譯器的相等功能。  
 
 此外，雖然 C# 版本更新通常會與主要 .NET Framework 版本一致，但是新語法和功能不需要繫結至該特定架構版本。 雖然新功能一定需要也要與 C# 修訂一起發行的新編譯器更新，但是每個特定功能都有自己的最低 .NET API 或通用語言執行平台需求，可讓它包含 NuGet 套件或其他程式庫以在舊版架構上執行。
  
 不論使用的 **-langversion** 設定為何，您都會使用目前版本的通用語言執行平台來建立 .exe 或 .dll。 其中一個例外狀況是 Friend 組件和 [-moduleassemblyname (C# 編譯器選項)](../../../csharp/language-reference/compiler-options/moduleassemblyname-compiler-option.md)，這些都是在 **-langversion:ISO-1** 下運作。  
 
 如需其他方式來指定 C# 語言版本，請參閱[選取 C# 語言版本](../configure-language-version.md)主題。
  
 如需如何以程式設計方式設定這個編譯器選項的詳細資訊，請參閱 <xref:VSLangProj80.CSharpProjectConfigurationProperties3.LanguageVersion%2A>。  
    
## <a name="see-also"></a>請參閱  
 [C# 編譯器選項](index.md)  
 [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)  
 
### <a name="c-language-specification"></a>C# 語言規格

|版本|連結|描述|
|-------|----|-----------|
|C# 1.0|[下載 DOC](http://download.microsoft.com/download/a/9/e/a9e229b9-fee5-4c3e-8476-917dee385062/csharp%20language%20specification%20v1.0.doc)|C# 語言規格版本 1.0：Microsoft Corporation|
|C# 1.2|[下載 DOC](http://download.microsoft.com/download/5/e/5/5e58be0a-b02b-41ac-a4a3-7a22286214ff/csharp%20language%20specification%20v1.2.doc)|C# 語言規格版本 1.2：Microsoft Corporation|
|C# 2.0|[下載 PDF](https://www.ecma-international.org/publications/files/ECMA-ST-ARCH/Ecma-334%204th%20edition%20June%202006.pdf)|標準 ECMA-334 第 4 版|
|C# 3.0|[下載 DOC](http://download.microsoft.com/download/3/8/8/388e7205-bc10-4226-b2a8-75351c669b09/CSharp%20Language%20Specification.doc)|C# 語言規格版本 3.0：Microsoft Corporation|
|C# 5.0|[下載 PDF](https://www.ecma-international.org/publications/files/ECMA-ST/Ecma-334.pdf)|標準 ECMA-334 第 5 版|
|C# 6.0|[連結](../language-specification/index.md)|C# 語言規格版本 6 - 非官方草稿：.NET Foundation|
|C# 7.0 與更新版本||目前無法使用|

### <a name="minimum-compiler-version-needed-to-support-all-language-features"></a>支援所有語言功能所需的最低編譯器版本   
[↩](#TISO1)<a name="FISO1">ISO1</a>：Microsoft Visual Studio/Build Tools .Net 2002 或配套 .Net Framework 1.0 編譯器     
[↩](#TISO2)<a name="FISO2">ISO2</a>：Microsoft Visual Studio/Build Tools 2005 或配套 .Net Framework 2.0 編譯器    
[↩](#TCS3)<a name="FCS3">CS3</a>：Microsoft Visual Studio/Build Tools 2008 或配套 .Net Framework 3.5 編譯器    
[↩](#TCS4)<a name="FCS4">CS4</a>：Microsoft Visual Studio/Build Tools 2010 或配套 .Net Framework 4.0 編譯器    
[↩](#TCS5)<a name="FCS5">CS5</a>：Microsoft Visual Studio/Build Tools 2012 或配套 .Net Framework 4.5 編譯器    
[↩](#TCS6)<a name="FCS6">CS6</a>：Microsoft Visual Studio/Build Tools 2015    
[↩](#TCS7)<a name="FCS7">CS7</a>：Microsoft Visual Studio/Build Tools 2017   
[↩](#TCS71)<a name="FCS71">CS71</a>：Microsoft Visual Studio/Build Tools 2017，15.3 版    
[↩](#TCS72)<a name="FCS72">CS72</a>：Microsoft Visual Studio/Build Tools 2017，15.5 版    
[↩](#TCS73)<a name="FCS73">CS73</a>：Microsoft Visual Studio/Build Tools 2017，15.7 版    

<!--- Uncomment and add to the above when they become officially released
[↩](#TCS8)<a name="FCS8">CS8</a>: Microsoft Visual Studio/Build Tools 20??    
-->
