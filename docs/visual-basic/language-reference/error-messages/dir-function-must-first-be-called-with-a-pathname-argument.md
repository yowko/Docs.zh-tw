---
title: '&#39;Dir&#39;函式必須先呼叫&#39;PathName&#39;引數'
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: f7e9ef9cc6309f24ae9f8963e910b41180c029b7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54518484"
---
# <a name="39dir39-function-must-first-be-called-with-a-39pathname39-argument"></a>&#39;Dir&#39;函式必須先呼叫&#39;PathName&#39;引數
初始呼叫`Dir`函式不包含`PathName`引數。 第一次呼叫`Dir`必須包含`PathName`，但後續呼叫`Dir`不需要包含參數，以擷取下一個項目。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  提供`PathName`函式呼叫中的引數。  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
