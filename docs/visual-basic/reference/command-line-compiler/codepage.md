---
title: -codepage
ms.date: 03/09/2018
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
ms.openlocfilehash: 769f3586ddef7f430fa96d6101b250a5bbc4e26c
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91065732"
---
# <a name="-codepage-visual-basic"></a>-字碼頁 (Visual Basic) 

指定編譯過程中所有原始程式碼檔使用的字碼頁。  
  
## <a name="syntax"></a>語法  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`id`|必要。 編譯器會使用指定的字碼頁 `id` 來解讀原始程式檔的編碼。|  
  
## <a name="remarks"></a>備註  

 若要編譯以特定編碼儲存的原始程式碼，您可以使用 `-codepage` 來指定應使用的字碼頁。 此 `-codepage` 選項會套用至您編譯中的所有原始程式碼檔。 如需詳細資訊，請參閱 [.NET Framework 中的字元編碼](../../../standard/base-types/character-encoding.md)。  
  
 `-codepage`如果使用目前的 ANSI 字碼頁、Unicode 或 utf-8 搭配簽章來儲存原始程式碼檔，則不需要此選項。 Visual Studio 預設會將所有原始程式碼檔儲存為目前的 ANSI 字碼頁，除非使用者在 [ **編碼** ] 對話方塊中指定另一種編碼方式。 Visual Studio 使用 [ **編碼** ] 對話方塊來開啟另一個字碼頁所儲存的原始程式碼檔案。  
  
> [!NOTE]
> `-codepage`選項無法在 Visual Studio 開發環境中使用; 只有在從命令列編譯時，才能使用此選項。  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
