---
title: -optimize
ms.date: 07/20/2015
helpviewer_keywords:
- optimize compiler option [Visual Basic]
- /optimize compiler option [Visual Basic]
- optimization [Visual Basic], enabling
- -optimize compiler option [Visual Basic]
ms.assetid: fcba4a97-3622-4b87-a891-0f77deab4998
ms.openlocfilehash: d4b50d56373676bf78a7591102095209401c907d
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91097588"
---
# <a name="-optimize"></a>-optimize

啟用或停用編譯器優化。  
  
## <a name="syntax"></a>語法  
  
```console  
-optimize[ + | - ]  
```  
  
## <a name="arguments"></a>引數  
  
|詞彙|定義|  
|---|---|  
|`+` &#124; `-`|選擇性。 `-optimize-`選項會停用編譯器優化。 `-optimize+`選項會啟用優化。 根據預設，會停用最佳化。|  
  
## <a name="remarks"></a>備註  

 編譯器最佳化可讓您的輸出檔案變得更小、更快、更有效率。 不過，因為優化會導致輸出檔中的程式碼重新排列，所以 `-optimize+` 很難進行偵錯工具。  
  
 針對元件產生的所有模組都 `-target:module` 必須使用與元件相同的 `-optimize` 設定。 如需詳細資訊，請參閱 [-目標 (Visual Basic) ](target.md)。  
  
 您可以結合 `-optimize` 和 `-debug` 選項。  
  
|在 Visual Studio 整合式開發環境中設定-優化|  
|---|  
|1. 在 **方案總管**中選取專案。 按一下 [專案] 功能表上的 [屬性]。<br />     <br />2. 按一下 [ **編譯** ] 索引標籤。<br />3. 按一下 [ **Advanced** ] 按鈕。<br />4. 修改 [ **啟用優化** ] 核取方塊。|  
  
## <a name="example"></a>範例  

 下列程式碼會編譯 `T2.vb` 並啟用編譯器優化。  
  
```console
vbc t2.vb -optimize  
```  
  
## <a name="see-also"></a>另請參閱

- [Visual Basic 命令列編譯器](index.md)
- [-debug (Visual Basic) ](debug.md)
- [編譯命令列的範例](sample-compilation-command-lines.md)
- [-目標 (Visual Basic) ](target.md)
