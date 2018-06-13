---
title: '&#39;Dir&#39;函式必須先呼叫&#39;PathName&#39;引數'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 3a271d7c2c2f7b98bae8f3f6fa9b67b65e3548f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585456"
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a>&#39;Dir&#39;函式必須先呼叫&#39;PathName&#39;引數
初始呼叫`Dir`函式不包含`PathName`引數。 第一次呼叫`Dir`必須包含`PathName`，但後續呼叫`Dir`不需要包含參數，以擷取下一個項目。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  提供`PathName`函式呼叫中的引數。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
