---
title: 呼叫 'Dir' 函式一定要有 'PathName' 引數
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 1064a44f7c266b9dcce05dfddedef6bb1e919999
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874459"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>呼叫 'Dir' 函式一定要有 'PathName' 引數

函數的初始呼叫不 `Dir` 包含 `PathName` 引數。 的第一個呼叫 `Dir` 必須包含 `PathName` ，但後續呼叫 `Dir` 不需要包含參數來取出下一個專案。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1. `PathName`在函式呼叫中提供引數。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
