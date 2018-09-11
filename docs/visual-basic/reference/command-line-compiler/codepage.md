---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: fda75383435fdff718d1d50bc8583afc9858e7e2
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2018
ms.locfileid: "44360938"
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)
指定編譯過程中所有原始程式碼檔使用的字碼頁。  
  
## <a name="syntax"></a>語法  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`id`|必要。 編譯器會使用指定的字碼頁`id`來解譯原始程式檔的編碼方式。|  
  
## <a name="remarks"></a>備註  
 若要編譯原始程式碼，以特定的編碼方式儲存，您可以使用`-codepage`指定應該使用的字碼頁。 `-codepage`選項會套用至您所編譯的所有原始程式碼檔案。 如需詳細資訊，請參閱 < [.NET Framework 中的字元編碼](../../../standard/base-types/character-encoding.md)。  
  
 `-codepage`如果原始程式檔已儲存的簽章中使用目前的 ANSI 字碼頁、 Unicode 或 utf-8，則不需要 選項。 Visual Studio 會儲存所有的原始程式檔與目前的 ANSI 字碼頁預設情況下，除非使用者指定中的另一個編碼**編碼** 對話方塊。 Visual Studio 會使用**編碼**對話方塊以開啟原始程式碼檔使用不同的字碼頁儲存。  
  
> [!NOTE]
>  `-codepage`選項不是從 Visual Studio 開發環境中使用; 只有在從命令列編譯時均可使用。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
