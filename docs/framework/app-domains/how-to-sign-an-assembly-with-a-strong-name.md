---
title: 作法：使用強式名稱簽署組件
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, signing with strong names
- signing assemblies
- assemblies [.NET Framework], signing
- assemblies [.NET Framework], strong-named
ms.assetid: 2c30799a-a826-46b4-a25d-c584027a6c67
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b109ec82d139e3b3eb321c90d5f41dd1eae216f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927925"
---
# <a name="how-to-sign-an-assembly-with-a-strong-name"></a>作法：使用強式名稱簽署組件
以下是幾種以強式名稱簽署組件的方式：  
  
- 使用 Visual Studio 中，專案之 [ **屬性** ] 對話方塊中的 [ **簽署** ] 索引標籤。 這是最簡單、最方便以強式名稱簽署組件的方式。  
  
- 透過使用 [組件連結器 (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) 將 .NET Framework 程式碼模組 (.netmodule 檔) 與金鑰檔連結在一起。  
  
- 使用組件屬性將強式名稱資訊插入您的程式碼。 您可以使用 <xref:System.Reflection.AssemblyKeyFileAttribute> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性，視使用的金鑰檔所在位置而定。  
  
- 使用編譯器選項。  
  
 您必須使用密碼編譯金鑰組將組件簽署為強式名稱。 如需建立金鑰組的詳細資訊，請參閱[如何：建立公開/私密金鑰組](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)。  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-visual-studio"></a>若要使用 Visual Studio 建立組件並以強式名稱簽署組件  
  
1. 在 **方案總管**中，開啟專案的捷徑功能表，然後選擇 [屬性]  。  
  
2. 選擇 [ **簽署** ] 索引標籤。  
  
3. 選取 [簽署組件]  方塊。  
  
4. 在 [選擇強式名稱金鑰檔]  方塊中，選擇 [\<瀏覽...>]  ，然後巡覽至金鑰檔。 若要建立新的金鑰檔，請選擇 [\<新增...>]  ，並且在 [建立強式名稱金鑰]  對話方塊中輸入其名稱。  
  
> [!NOTE]
> 若要[延遲簽署組件](../../../docs/framework/app-domains/delay-sign-assembly.md)，請選擇公開金鑰檔案。  
  
### <a name="to-create-and-sign-an-assembly-with-a-strong-name-by-using-the-assembly-linker"></a>若要使用組件連結器建立組件並以強式名稱簽署組件  
  
- 在 [Visual Studio 開發人員命令提示字元](../../../docs/framework/tools/developer-command-prompt-for-vs.md)中鍵入下列命令：  
  
     **al** **/out:** \<*assemblyName*>  *\<moduleName>* **/keyfile:** \<*keyfileName*>  
  
     其中：  
  
     *assemblyName*  
     組件連結器將發出的強式簽署組件名稱 (.dll 或 .exe 檔)。  
  
     *moduleName*  
     .NET Framework 程式碼模組 (.netmodule 檔) 的名稱，其中包括一或多個類型。 您可以在 C# 或 Visual Basic 中使用 `/target:module` 參數編譯程式碼，藉此建立 .netmodule 檔。  
  
     *keyfileName*  
     包含金鑰組之容器或檔案的名稱。 組件連結器會解譯與目前目錄相關的相對路徑。  
  
 下列範例將使用金鑰檔 `MyAssembly.dll` 以強式名稱簽署組件 `sgKey.snk`。  
  
```  
al /out:MyAssembly.dll MyModule.netmodule /keyfile:sgKey.snk  
```  
  
 如需這項工具的詳細資訊，請參閱 [組件連結器](../../../docs/framework/tools/al-exe-assembly-linker.md)。  
  
#### <a name="to-sign-an-assembly-with-a-strong-name-by-using-attributes"></a>若要使用屬性以強式名稱簽署組件  
  
1. 將 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=nameWithType> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性加入至您的原始程式碼檔，並指定容器或檔案名稱，其中包含以強式名稱簽署組件時所使用的金鑰組。  
  
2. 以一般方式編譯原始程式碼檔。  
  
> [!NOTE]
> C# 和 Visual Basic 編譯器在原始程式碼中遇到 <xref:System.Reflection.AssemblyKeyFileAttribute> 或 <xref:System.Reflection.AssemblyKeyNameAttribute> 屬性時，會發出編譯器警告 (分別為 CS1699 和 BC41008)。 您可以忽略這些警告。  
  
 下列範例將搭配稱為 <xref:System.Reflection.AssemblyKeyFileAttribute> 的金鑰檔使用 `keyfile.snk`屬性，這個金鑰檔位於編譯組件所在的目錄中。  
  
 [!code-cpp[AssemblyName_KeyPair#21](../../../samples/snippets/cpp/VS_Snippets_CLR/AssemblyName_KeyPair/CPP/keyfileattrib.cpp#21)]
 [!code-csharp[AssemblyName_KeyPair#21](../../../samples/snippets/csharp/VS_Snippets_CLR/AssemblyName_KeyPair/CS/keyfileattrib.cs#21)]
 [!code-vb[AssemblyName_KeyPair#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/AssemblyName_KeyPair/VB/keyfileattrib.vb#21)]  
  
 您也可以在編譯原始程式檔時延遲簽署組件。 如需詳細資訊，請參閱 [延遲簽署組件](../../../docs/framework/app-domains/delay-sign-assembly.md)。  
  
### <a name="to-sign-an-assembly-with-a-strong-name-by-using-the-compiler"></a>若要使用編譯器以強式名稱簽署組件  
  
- 在 C# 和 Visual Basic 中使用 `/keyfile` 或 `/delaysign` 編譯器選項，或是在 C++ 中使用 `/KEYFILE` 或 `/DELAYSIGN` 連結器選項編譯原始程式碼檔。 在選項名稱後面加上冒號和金鑰檔的名稱。 使用命令列編譯器時，您可以將金鑰檔複製到包含您的原始程式碼檔的目錄中。  
  
     如需延遲簽署的詳細資訊，請參閱 [Delay Signing an Assembly](../../../docs/framework/app-domains/delay-sign-assembly.md)。  
  
     下列範例將使用 C# 編譯器，並且使用金鑰檔 `UtilityLibrary.dll` 以強式名稱簽署 `sgKey.snk` 組件。  
  
    ```  
    csc /t:library UtilityLibrary.cs /keyfile:sgKey.snk  
    ```  
  
## <a name="see-also"></a>另請參閱

- [建立和使用強式名稱的組件](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
- [如何：建立公開/私密金鑰組](../../../docs/framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Al.exe (組件連結器)](../../../docs/framework/tools/al-exe-assembly-linker.md)
- [延遲簽署組件](../../../docs/framework/app-domains/delay-sign-assembly.md)
- [管理組件和資訊清單簽署](/visualstudio/ide/managing-assembly-and-manifest-signing)
- [專案設計工具、簽署頁面](/visualstudio/ide/reference/signing-page-project-designer)
