---
title: 如何：使用強式名稱對程式集進行簽名
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 9998e69e8bf1505bcfc7a9103e9d89616dad9633
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160309"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>如何：使用強式名稱對程式集進行簽名

> [!NOTE]
> 儘管 .NET Core 支援強命名程式集，並且 .NET Core 庫中的所有程式集都已簽名，但大多數協力廠商程式集不需要強名稱。 有關詳細資訊，請參閱 GitHub 上的[強式名稱簽名](https://github.com/dotnet/runtime/blob/master/docs/project/strong-name-signing.md)。

以下是幾種以強式名稱簽署組件的方式：  
  
- 使用 Visual Studio 中，專案之 [ **屬性** ] 對話方塊中的 [ **簽署** ] 索引標籤。 這是最簡單、最方便以強式名稱簽署組件的方式。  
  
- 通過使用[程式集連結器 （Al.exe）](../../framework/tools/al-exe-assembly-linker.md)將 .NET 框架代碼模組 *（.netmodule*檔）與金鑰檔連結。  
  
- 使用組件屬性將強式名稱資訊插入您的程式碼。 您可以使用 <xref:System.Reflection.AssemblyKeyFileAttribute> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性，視使用的金鑰檔所在位置而定。  
  
- 使用編譯器選項。  
  
 您必須使用密碼編譯金鑰組將組件簽署為強式名稱。 有關創建金鑰組的詳細資訊，請參閱[如何：創建公開金鑰對](create-public-private-key-pair.md)。  
  
## <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>使用 Visual Studio 創建具有強式名稱的程式集並簽名  
  
1. 在 **方案總管**中，開啟專案的捷徑功能表，然後選擇 [屬性] ****。  
  
2. 選擇 [ **簽署** ] 索引標籤。  
  
3. 選取 [簽署組件]**** 方塊。  
  
4. 在 **"選擇強式名稱鍵檔**"框中，選擇 **"流覽**"，然後導航到金鑰檔。 要創建新的金鑰檔，請在 **"創建強式名稱鍵**"對話方塊中選擇 **"新建**"並輸入其名稱。  
  
> [!NOTE]
> 若要[延遲簽署組件](delay-sign.md)，請選擇公開金鑰檔案。  
  
### <a name="create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>使用程式集連結器創建並使用強式名稱創建和簽名  
  
在[視覺化工作室的開發人員命令提示符](../../framework/tools/developer-command-prompt-for-vs.md)中，輸入以下命令：  

**al** **/out：**\<*程式集名稱*> *\<模組名稱>* **/鍵檔：**\<*金鑰檔案名稱*>  

其中：  

- *程式集名稱*是程式集連結器將發出的強簽名程式集 *（.dll*或 *.exe*檔）的名稱。  
  
- *模組名稱*是 .NET 框架代碼模組 *（.netmodule*檔）的名稱，其中包含一個或多個類型。 您可以通過使用 C# 或 Visual Basic 中的`/target:module`交換器編譯代碼來創建 *.netmodule*檔。
  
- *keyfileName*是包含金鑰組的容器或檔的名稱。 程式集連結器解釋與目前的目錄相關的相對路徑。  

下面的示例使用金鑰檔*sgKey.snk*使用強式名稱對程式集*MyAssembly.dll*進行標記。  

```console
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
如需這項工具的詳細資訊，請參閱 [組件連結器](../../framework/tools/al-exe-assembly-linker.md)。  
  
## <a name="sign-an-assembly-with-a-strong-name-by-using-attributes"></a>使用屬性對具有強式名稱的程式集進行簽名  
  
1. 將 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性加入至您的原始程式碼檔，並指定容器或檔案名稱，其中包含以強式名稱簽署組件時所使用的金鑰組。  

2. 以一般方式編譯原始程式碼檔。  

   > [!NOTE]
   > C# 和 Visual Basic 編譯器在原始程式碼中遇到 <xref:System.Reflection.AssemblyKeyFileAttribute> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性時，會發出編譯器警告 (分別為 CS1699 和 BC41008)。 您可以忽略這些警告。  

下面的示例使用該<xref:System.Reflection.AssemblyKeyFileAttribute>屬性與一個鍵檔稱為*keyfile.snk*，它位於編譯器集的目錄中。  

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

您也可以在編譯原始程式檔時延遲簽署組件。 有關詳細資訊，請參閱[延遲簽名程式集](delay-sign.md)。  

## <a name="sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>使用編譯器對具有強式名稱的程式集進行簽名  

在 C# 和 Visual Basic 中使用 `/keyfile` 或 `/delaysign` 編譯器選項，或是在 C++ 中使用 `/KEYFILE` 或 `/DELAYSIGN` 連結器選項編譯原始程式碼檔。 在選項名稱後面加上冒號和金鑰檔的名稱。 使用命令列編譯器時，您可以將金鑰檔複製到包含您的原始程式碼檔的目錄中。  

有關延遲簽名的資訊，請參閱[延遲簽名程式集](delay-sign.md)。  

下面的示例使用 C# 編譯器並使用金鑰檔*sgKey.snk*使用強式名稱對程式集*實用程式庫.dll*進行簽名。  

```cmd
csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
```  

## <a name="see-also"></a>另請參閱

- [建立和使用強式名稱的組件](create-use-strong-named.md)
- [如何：建立公開/私密金鑰組](create-public-private-key-pair.md)
- [Al.exe (組件連結器)](../../framework/tools/al-exe-assembly-linker.md)
- [延遲簽署組件](delay-sign.md)
- [管理程式集和清單簽名](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [專案設計工具、簽署頁](/visualstudio/ide/reference/signing-page-project-designer)
