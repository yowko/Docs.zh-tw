---
title: 作法：建立公開/私密金鑰組
ms.date: 08/20/2019
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET Framework], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 62c38494e29541bd490d69ccc8de485217b9514a
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991695"
---
# <a name="how-to-create-a-public-private-key-pair"></a>作法：建立公開/私密金鑰組

若要使用強式名稱簽署組件，您必須擁有公開/私密金鑰組。 這個公用和私密的密碼編譯金鑰組將在編譯期間用來建立強式名稱的組件。 您可以使用[強式名稱工具 (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) 來建立金鑰組。 金鑰組檔案的副檔名通常為 *.snk* 。

> [!NOTE]
> 在 Visual Studio 中， C#和 Visual Basic 專案屬性頁包含 [**簽署**] 索引標籤，可讓您選取現有的金鑰檔，或在不使用*sn.exe*的情況下產生新的金鑰檔。 在 Visual C++ 中，您可以在 [屬性頁] 視窗的 [組態屬性] 區段之 [連結器] 區段的 [進階] 屬性頁中，指定現有金鑰檔的位置。 從 Visual Studio 2005 開始<xref:System.Reflection.AssemblyKeyFileAttribute> ，使用屬性來識別金鑰檔案組已過時。

## <a name="create-a-key-pair"></a>建立金鑰組

若要建立金鑰組，請在命令提示字元中輸入下列命令：

**sn –k** \<*file name*>

在這個命令中，*file name* 是含有金鑰組之輸出檔案的名稱。

下列範例會建立名為*sgKey*的金鑰組。

```cmd
sn -k sgKey.snk
```

如果您想要延遲簽署組件，而且您控制了整個金鑰組 (這大致是發生在測試案例中的情形)，您可以使用下列命令來產生金鑰組，然後從金鑰組解壓縮公開金鑰到個別的檔案中。 首先，請建立金鑰組：

```cmd
sn -k keypair.snk
```

接下來，從金鑰組解壓縮公開金鑰，並將公開金鑰複製到個別的檔案中：

```cmd
sn -p keypair.snk public.snk
```

建立金鑰組之後，您必須將檔案放到可使用強式名稱簽署工具尋找到的位置。

使用強式名稱簽署組件時，[組件連結器 (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) 會尋找金鑰檔的相關目前目錄和輸出目錄。 使用命令列編譯器時，您可以只要將金鑰複製到含有您的程式模組的目前目錄即可。

如果您正在使用舊版的 Visual Studio，而該版本在專案屬性 (Property) 內沒有 [簽署] 索引標籤，則建議的金鑰檔位置為專案目錄，並指定如下所示的檔案屬性 (Attribute)：

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a>另請參閱

- [建立和使用強式名稱的元件](create-use-strong-named.md)
