---
title: 作法：使用強式名稱簽署元件
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 527fd68ef40e152b57a1fc98113094d3b41fbaae
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973058"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>作法：使用強式名稱簽署元件

> [!NOTE]
> 雖然 .NET Core 支援強式名稱的元件，而且 .NET Core 程式庫中的所有元件都已簽署，但大部分的協力廠商元件都不需要強名稱。 如需詳細資訊，請參閱 GitHub 上的[強式名稱簽署](https://github.com/dotnet/corefx/blob/master/Documentation/project-docs/strong-name-signing.md)。

以下是幾種以強式名稱簽署組件的方式：  
  
- 使用 Visual Studio 中，專案之 [ **屬性** ] 對話方塊中的 [ **簽署** ] 索引標籤。 這是最簡單、最方便以強式名稱簽署組件的方式。  
  
- 藉由使用[元件連結器（al.exe）](../../framework/tools/al-exe-assembly-linker.md) ，將 .NET Framework 程式碼模組（ *.netmodule*檔）與金鑰檔連結。  
  
- 使用組件屬性將強式名稱資訊插入您的程式碼。 您可以使用 <xref:System.Reflection.AssemblyKeyFileAttribute> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性，視使用的金鑰檔所在位置而定。  
  
- 使用編譯器選項。  
  
 您必須使用密碼編譯金鑰組將組件簽署為強式名稱。 如需建立金鑰組的詳細資訊，請參閱[如何：建立公開/私密金鑰組](create-public-private-key-pair.md)。  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>使用 Visual Studio，以強式名稱建立並簽署元件  
  
1. 在 **方案總管**中，開啟專案的捷徑功能表，然後選擇 [屬性]。  
  
2. 選擇 [ **簽署** ] 索引標籤。  
  
3. 選取 [簽署組件] 方塊。  
  
4. 在 [**選擇強式名稱金鑰**檔案] 方塊中，選擇 **[流覽]** ，然後流覽至金鑰檔。 若要建立新的金鑰檔，請選擇 [**新增**]，然後在 [**建立強式名稱金鑰**] 對話方塊中輸入其名稱。  
  
> [!NOTE]
> 若要[延遲簽署組件](delay-sign.md)，請選擇公開金鑰檔案。  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>使用元件連結器建立元件並以強式名稱簽署  
  
在[Visual Studio 的開發人員命令提示字元](../../framework/tools/developer-command-prompt-for-vs.md)中，輸入下列命令：  

**al** **/out:** \<*assemblyName*>  *\<moduleName>* **/keyfile:** \<*keyfileName*>  

其中：  

- *assemblyName*是元件連結器將發出的強式簽署元件（ *.dll*或 *.exe*檔案）的名稱。  
  
- *moduleName*是包含一或多個類型 .NET Framework 程式碼模組（ *.netmodule*檔案）的名稱。 您可以使用或 Visual Basic 中`/target:module` C#的參數編譯器代碼，來建立 .netmodule 檔案。
  
- *keyfileName*是包含金鑰組的容器或檔案名。 元件連結器會根據目前目錄來解讀相對路徑。  

下列範例會使用金鑰檔*sgKey*，以強式名稱簽署元件*MyAssembly* 。  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
如需這項工具的詳細資訊，請參閱 [組件連結器](../../framework/tools/al-exe-assembly-linker.md)。  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a>使用屬性以強式名稱簽署元件  
  
1. 將 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性加入至您的原始程式碼檔，並指定容器或檔案名稱，其中包含以強式名稱簽署組件時所使用的金鑰組。  
   
2. 以一般方式編譯原始程式碼檔。  
   
   > [!NOTE]
   > C# 和 Visual Basic 編譯器在原始程式碼中遇到 <xref:System.Reflection.AssemblyKeyFileAttribute> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性時，會發出編譯器警告 (分別為 CS1699 和 BC41008)。 您可以忽略這些警告。  

下列範例會使用<xref:System.Reflection.AssemblyKeyFileAttribute>屬性搭配名為*keyfile*的金鑰檔，此檔案位於編譯元件所在的目錄中。  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

您也可以在編譯原始程式檔時延遲簽署組件。 如需詳細資訊，請參閱[延遲簽署元件](delay-sign.md)。  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>使用編譯器以強式名稱簽署元件  

在 C# 和 Visual Basic 中使用 `/keyfile` 或 `/delaysign` 編譯器選項，或是在 C++ 中使用 `/KEYFILE` 或 `/DELAYSIGN` 連結器選項編譯原始程式碼檔。 在選項名稱後面加上冒號和金鑰檔的名稱。 使用命令列編譯器時，您可以將金鑰檔複製到包含您的原始程式碼檔的目錄中。  

如需延遲簽署的詳細資訊，請參閱[延遲簽署元件](delay-sign.md)。  

下列範例會使用C#編譯器，並使用金鑰檔*sgKey*，以強式名稱簽署元件*UtilityLibrary* 。  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a>另請參閱

- [建立和使用強式名稱的元件](create-use-strong-named.md)
- [如何：建立公開/私密金鑰組](create-public-private-key-pair.md)
- [Al.exe (組件連結器)](../../framework/tools/al-exe-assembly-linker.md)
- [延遲簽署元件](delay-sign.md)
- [管理組件與資訊清單簽署](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [專案設計工具、簽署頁](/visualstudio/ide/reference/signing-page-project-designer)
