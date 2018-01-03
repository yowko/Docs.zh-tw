---
title: "做為回呼方法，委派封送處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, Callback sample
- marshaling, Callback sample
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6d9269261c6c0ce7573e0a8e298111971ae591c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="marshaling-a-delegate-as-a-callback-method"></a>做為回呼方法，委派封送處理
此範例示範如何將委派傳遞至需要函式指標的 Unmanaged 函式。 委派是可保留方法參考的類別，並且相當於型別安全函式指標或回呼函式。  
  
> [!NOTE]
>  當您在呼叫內使用委派時，Common Language Runtime 會在該呼叫的期間防止對委派進行記憶體回收。 不過，如果 Unmanaged 函式儲存要在呼叫完成之後使用的委派，您必須手動防止記憶體回收，直到 Unmanaged 函式與委派一起完成之前。 如需詳細資訊，請參閱 [HandleRef 範例](http://msdn.microsoft.com/en-us/ab23b04e-1d53-4ec7-b27a-e892d9298959)和 [GCHandle 範例](http://msdn.microsoft.com/en-us/6acce798-0385-4ded-a790-77da842c113f)。  
  
 Callback 範例會使用下列 Unmanaged 函式和其原始函式宣告，如下所示：  
  
-   從 PinvokeLib.dll 匯出的 **TestCallBack**。  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   從 PinvokeLib.dll 匯出的 **TestCallBack2**。  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 [PinvokeLib.dll](http://msdn.microsoft.com/en-us/5d1438d7-9946-489d-8ede-6c694a08f614) 是自訂的 Unmanaged 程式庫，其中包含先前所列出函式的實作。  
  
 在此範例中，`LibWrap` 類別包含 `TestCallBack` 和 `TestCallBack2` 方法的 Managed 原型。 這兩種方法都會將委派當成參數傳遞給回呼函式。 委派的簽章必須符合它所參考之方法的簽章。 例如，`FPtr` 和 `FPtr2` 委派的簽章與 `DoSomething` 和 `DoSomething2` 方法相同。  
  
## <a name="declaring-prototypes"></a>宣告原型  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## <a name="calling-functions"></a>呼叫函式  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## <a name="see-also"></a>請參閱  
 [其他封送處理範例](http://msdn.microsoft.com/en-us/a915c948-54e9-4d0f-a525-95a77fd8ed70)  
 [平台叫用資料類型](http://msdn.microsoft.com/en-us/16014d9f-d6bd-481e-83f0-df11377c550f)  
 [在 Managed 程式碼中建立原型](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)
