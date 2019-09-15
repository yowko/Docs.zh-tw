---
title: -keycontainer (C# 編譯器選項)
ms.date: 05/16/2018
f1_keywords:
- /keycontainer
helpviewer_keywords:
- /keycontainer compiler option [C#]
- keycontainer compiler option [C#]
- -keycontainer compiler option [C#]
ms.assetid: b3982b6d-2382-4f7e-bebd-ce98eaa30763
ms.openlocfilehash: fead2d4296cfa6fb0195cb4b43f6448c0fc7e6a9
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970141"
---
# <a name="-keycontainer-c-compiler-options"></a>-keycontainer (C# 編譯器選項)
指定密碼編譯金鑰容器的名稱。  
  
## <a name="syntax"></a>語法  
  
```console  
-keycontainer:string  
```  
  
## <a name="arguments"></a>引數  
 `string`  
 強式名稱金鑰容器的名稱。  
  
## <a name="remarks"></a>備註  
 使用 **-keycontainer** 選項時，編譯器會建立可共用的元件。 編譯器會從指定的容器將公開金鑰插入至組件資訊清單，然後使用私密金鑰簽署最終組件。 若要產生金鑰檔，請在命令列中輸入 `sn -k file`。 `sn -i` 會將金鑰組安裝於容器中。 當編譯器在 CoreCLR 上執行時，不支援此選項。 若要在 CoreCLR 上建置時簽署組件，請使用 [-keyfile](keyfile-compiler-option.md) 選項。
  
 如果您使用 [-target:module](./target-module-compiler-option.md) 進行編譯，則在使用 [-addmodule](./addmodule-compiler-option.md) 將這個模組編譯為組件時，金鑰檔的名稱會保留在模組中並併入組件。  
  
 您也可以在任何 Microsoft 中繼語言 (MSIL) 模組的原始程式碼中，將這個選項指定為自訂屬性 (<xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=nameWithType>)。  
  
 您也可以使用 [-keyfile](./keyfile-compiler-option.md) 將加密資訊傳遞給編譯器。 如果您想要將公開金鑰新增至資訊清單，但希望等到測試過後再簽署組件，請使用 [-delaysign](./delaysign-compiler-option.md)。  
  
 如需詳細資訊，請參閱[建立和使用強式名稱的組件](../../../standard/assembly/create-use-strong-named.md)和[延遲簽署組件](../../../standard/assembly/delay-sign.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1. Visual Studio 開發環境無法使用這個編譯器選項。  
  
 您可以使用 <xref:VSLangProj.ProjectProperties.AssemblyKeyContainerName%2A>，以程式設計方式存取這個編譯器選項。  
  
## <a name="see-also"></a>另請參閱

- [C# 編譯器 -keyfile 選項](keyfile-compiler-option.md)
- [C# 編譯器選項](index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
