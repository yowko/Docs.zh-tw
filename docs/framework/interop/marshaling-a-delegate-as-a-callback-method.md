---
title: "做為回呼方法，委派封送處理 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "資料封送處理, 回呼範例"
  - "封送處理, 回呼範例"
ms.assetid: 6ddd7866-9804-4571-84de-83f5cc017a5a
caps.latest.revision: 13
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 13
---
# 做為回呼方法，委派封送處理
這個範例示範如何將委派傳遞至預期函式指標的 Unmanaged 函式。  委派是一種含有方法參考的類別，相當於型別安全函式指標或回呼函式 \(Callback Function\)。  
  
> [!NOTE]
>  當您在呼叫內使用委派時，在該呼叫期間，Common Language Runtime 會保護委派不被記憶體回收。  不過，如果 Unmanaged 函式儲存在呼叫完成之後所要使用的委派，您必須在 Unmanaged 函式完成委派之前手動防止記憶體回收。  如需詳細資訊，請參閱 [HandleRef 範例](http://msdn.microsoft.com/zh-tw/ab23b04e-1d53-4ec7-b27a-e892d9298959) 和 [GCHandle 範例](http://msdn.microsoft.com/zh-tw/6acce798-0385-4ded-a790-77da842c113f)。  
  
 回呼範例使用下列 Unmanaged 函式，顯示其原始函式宣告：  
  
-   從 PinvokeLib.dll 匯出 **TestCallBack**。  
  
    ```  
    void TestCallBack(FPTR pf, int value);  
    ```  
  
-   從 PinvokeLib.dll 匯出 **TestCallBack2**。  
  
    ```  
    void TestCallBack2(FPTR2 pf2, char* value);  
    ```  
  
 [PinvokeLib.dll](http://msdn.microsoft.com/zh-tw/5d1438d7-9946-489d-8ede-6c694a08f614) 是自訂的 Unmanaged 程式庫，包含先前列示之函式的實作。  
  
 在這個範例中，`LibWrap` 類別包含 `TestCallBack` 和 `TestCallBack2` 方法的 Managed 原型。  這兩個方法會將委派當成參數傳遞至回呼函式。  委派的簽章 \(Signature\) 必須符合它所參考的方法簽章。  例如，`FPtr` 和 `FPtr2` 委派具有相同於 `DoSomething` 與 `DoSomething2` 方法的簽章。  
  
## 宣告原型  
 [!code-cpp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#37)]
 [!code-csharp[Conceptual.Interop.Marshaling#37](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#37)]
 [!code-vb[Conceptual.Interop.Marshaling#37](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#37)]  
  
## 呼叫函式  
 [!code-cpp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/callback.cpp#38)]
 [!code-csharp[Conceptual.Interop.Marshaling#38](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/callback.cs#38)]
 [!code-vb[Conceptual.Interop.Marshaling#38](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/callback.vb#38)]  
  
## 請參閱  
 [Miscellaneous Marshaling Samples](http://msdn.microsoft.com/zh-tw/a915c948-54e9-4d0f-a525-95a77fd8ed70)   
 [Platform Invoke Data Types](http://msdn.microsoft.com/zh-tw/16014d9f-d6bd-481e-83f0-df11377c550f)   
 [在 Managed 程式碼中建立原型](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)