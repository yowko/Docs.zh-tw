---
title: -字碼頁 (Visual Basic)
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 383b6adae94c27efdd236de31ddfa8d16a6d4648
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-codepage-visual-basic"></a>-字碼頁 (Visual Basic)
指定編譯過程中所有原始程式碼檔使用的字碼頁。  
  
## <a name="syntax"></a>語法  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`id`|必要。 編譯器會使用所指定的字碼頁`id`解譯原始程式檔的編碼方式。|  
  
## <a name="remarks"></a>備註  
 若要編譯原始程式碼，以特定編碼方式儲存，您可以使用`-codepage`來指定應該使用的字碼頁。 `-codepage`選項適用於您所編譯的所有原始程式碼檔。 如需詳細資訊，請參閱[字元編碼方式在.NET Framework](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9)。  
  
 `-codepage`如果原始程式檔儲存具有簽章中使用目前的 ANSI 字碼頁、 Unicode 或 utf-8，則不需要選項。 Visual Studio 會儲存所有原始程式檔與目前的 ANSI 字碼頁根據預設，除非使用者另外指定其他編碼方式在**編碼** 對話方塊。 Visual Studio 會使用**編碼**對話方塊來開啟原始程式碼檔使用不同的字碼頁儲存。  
  
> [!NOTE]
>  `-codepage`選項不是從 Visual Studio 開發環境中使用; 其只有在從命令列編譯時。  
  
## <a name="see-also"></a>另請參閱  
 [Visual Basic 命令列編譯器](../../../visual-basic/reference/command-line-compiler/index.md)
