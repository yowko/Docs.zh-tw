---
title: -noconfig (C# 編譯器選項)
ms.date: 07/20/2015
f1_keywords:
- /noconfig
helpviewer_keywords:
- /noconfig compiler option [C#]
- csc.rsp
- -noconfig compiler option [C#]
- noconfig compiler option [C#]
ms.assetid: cd26967e-e494-4c8c-b5c9-af13b2f78b2e
ms.openlocfilehash: 2d6d0c52be2306292224d7831f8818c6f865f2f4
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602747"
---
# <a name="-noconfig-c-compiler-options"></a>-noconfig (C# 編譯器選項)
**-noconfig** 選項會指示編譯器不要使用 csc.rsp 檔案，該檔案位於與 csc.exe 檔案相同的目錄並從中載入。  
  
## <a name="syntax"></a>語法  
  
```console  
-noconfig  
```  
  
## <a name="remarks"></a>備註  
 csc.rsp 檔案參考了 .NET Framework 隨附的所有組件。 Visual Studio .NET 開發環境中所包含的實際參考視專案類型而定。  
  
 您可以修改 csc.rsp 檔案，並指定應併入每次從命令列使用 csc.exe 進行之編譯的其他編譯器選項 (除了 **-noconfig** 選項外)。  
  
 編譯器最後才會處理傳遞至 **csc** 命令的選項。 因此，命令列上的任何選項會覆寫 csc.rsp 檔案中相同選項的設定。  
  
 如果您不想要編譯器尋找和使用 csc.rsp 檔案中的設定，請指定 **-noconfig**。  
  
 Visual Studio 不提供這個編譯器選項，您亦無法以程式設計方式變更。  
  
## <a name="see-also"></a>另請參閱

- [C# 編譯器選項](./index.md)
- [管理專案和方案屬性](/visualstudio/ide/managing-project-and-solution-properties)
