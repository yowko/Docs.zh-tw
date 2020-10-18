---
title: 呼叫 'Dir' 函式一定要有 'PathName' 引數
ms.date: 07/20/2015
f1_keywords:
- vbrDIR_IllegalCall
ms.assetid: 7b5d149f-be91-4ac3-8262-86a360894e7d
ms.openlocfilehash: 7f8191b0ef5452fcf6f3a20c3e0f28ca84ef9c4a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163424"
---
# <a name="dir-function-must-first-be-called-with-a-pathname-argument"></a>呼叫 'Dir' 函式一定要有 'PathName' 引數

函數的初始呼叫不 `Dir` 包含 `PathName` 引數。 的第一個呼叫 `Dir` 必須包含 `PathName` ，但後續呼叫 `Dir` 不需要包含參數來取出下一個專案。

## <a name="to-correct-this-error"></a>更正這個錯誤

- `PathName`在函式呼叫中提供引數。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileSystem.Dir%2A>
