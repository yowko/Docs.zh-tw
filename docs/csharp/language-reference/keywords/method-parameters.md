---
title: 方法參數 - C# 參考
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#], parameters
- method parameters [C#]
- parameters [C#]
ms.assetid: 680e39ff-775b-48b0-9f47-4186a5bfc4a1
ms.openlocfilehash: 4011cbd3bc9306b64df87b1fcde48f1f41df8240
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602035"
---
# <a name="method-parameters-c-reference"></a>方法參數 (C# 參考)

為沒有 [in](./in-parameter-modifier.md)、[ref](./ref.md) 或 [out](./out-parameter-modifier.md) 的方法宣告之參數，會以值的方式傳遞到呼叫的方法。 該值可以在方法中進行變更，但控制權傳回給呼叫程序時，不會保留已變更值。 使用方法參數關鍵字，即可變更此行為。  
  
 本節描述在您宣告方法參數時可以使用的關鍵字：  
  
- [params](./params.md) 指定這個參數可以接受可變數目的引數。
  
- [in](./in-parameter-modifier.md) 指定這個參數是傳址方式傳遞，但只會由所呼叫的方法讀取。
  
- [ref](./ref.md) 指定這個參數是傳址方式傳遞，且可以由所呼叫的方法讀取或寫入。
  
- [out](./out-parameter-modifier.md) 指定這個參數是傳址方式傳遞，且由所呼叫的方法寫入。
  
## <a name="see-also"></a>另請參閱

- [C# 參考](../index.md)
- [C# 程式設計指南](../../programming-guide/index.md)
- [C# 關鍵字](./index.md)
