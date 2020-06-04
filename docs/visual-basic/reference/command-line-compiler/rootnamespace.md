---
title: -rootnamespace
ms.date: 03/13/2018
f1_keywords:
- /rootnamespace
- rootnamespace
helpviewer_keywords:
- /rootnamespace compiler option [Visual Basic]
- -rootnamespace compiler option [Visual Basic]
- rootnamespace compiler option [Visual Basic]
ms.assetid: e9245edf-6bef-420d-a7c7-324117752783
ms.openlocfilehash: b6a2f3ba0772d8f8c8c6a762a1be01703d21b778
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403131"
---
# <a name="-rootnamespace"></a>-rootnamespace
指定所有類型宣告的命名空間。  
  
## <a name="syntax"></a>語法  
  
```console  
-rootnamespace:namespace  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`namespace`|要用來括住目前專案之所有類型宣告的命名空間名稱。|  
  
## <a name="remarks"></a>備註  
 如果您使用 Visual Studio 可執行檔（Devenv）來編譯在 Visual Studio 整合式開發環境中建立的專案，請使用 `-rootnamespace` 來指定屬性的值 <xref:VSLangProj80.VBProjectProperties3.RootNamespace%2A> 。 如需詳細資訊，請參閱[Devenv 命令列參數](/visualstudio/ide/reference/devenv-command-line-switches)。  
  
 使用 common language runtime MSIL 解譯器（ `Ildasm.exe` ）來查看輸出檔案中的命名空間名稱。  
  
|在 Visual Studio 的整合式開發環境中設定-rootnamespace|  
|---|  
|1. 在**方案總管**中選取專案。 按一下 [專案]**** 功能表上的 [屬性]****。 <br />2. 按一下 [**應用程式**] 索引標籤。<br />3. 修改 [**根命名空間**] 方塊中的值。|  
  
## <a name="example"></a>範例  
 下列程式碼會編譯 `In.vb` 並括住命名空間中的所有類型宣告 `mynamespace` 。  
  
```console
vbc -rootnamespace:mynamespace in.vb  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [Ildasm （IL 解譯器）](../../../framework/tools/ildasm-exe-il-disassembler.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
