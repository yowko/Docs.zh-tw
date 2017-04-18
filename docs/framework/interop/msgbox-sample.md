---
title: "MsgBox 範例 | Microsoft Docs"
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
  - "資料封送處理, MsgBox 範例"
  - "封送處理, MsgBox 範例"
ms.assetid: 9e0edff6-cc0d-4d5c-a445-aecf283d9c3a
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# MsgBox 範例
這個範例示範如何以傳值方式將字串型別當成 In 參數傳遞，以及何時使用 <xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>、<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> 和 <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling> 欄位。  
  
 MsgBox 範例使用下列 Unmanaged 函式，顯示其原始函式宣告：  
  
-   從 User32.dll 匯出的 **MessageBox**。  
  
    ```  
    int MessageBox(HWND hWnd, LPCTSTR lpText, LPCTSTR lpCaption,   
       UINT uType);  
    ```  
  
 在這個範例中，`LibWrap` 類別包含由 `MsgBoxSample` 類別呼叫的每一個 Unmanaged 函式的 Managed 原型。  對於相同的 Unmanaged 函式，Managed 原型方法 `MsgBox`、`MsgBox2` 和 `MsgBox3` 有不同的宣告。  
  
 `MsgBox2` 的宣告會在訊息方塊中產生不正確的輸出，因為以 ANSI 指定的字元型別與進入點 \(Entry Point\) `MessageBoxW` \(即 Unicode 函式的名稱\) 不相符。  `MsgBox3` 的宣告會在 **EntryPoint**、**CharSet** 和 **ExactSpelling** 欄位之間建立一個不相符。  當呼叫時，`MsgBox3` 會擲回例外狀況。  如需字串命名和名稱封送處理的詳細資訊，請參閱[指定字元集](../../../docs/framework/interop/specifying-a-character-set.md)。  
  
## 宣告原型  
 [!code-cpp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#5)]
 [!code-csharp[Conceptual.Interop.Marshaling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#5)]
 [!code-vb[Conceptual.Interop.Marshaling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#5)]  
  
## 呼叫函式  
 [!code-cpp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/msgbox.cpp#6)]
 [!code-csharp[Conceptual.Interop.Marshaling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/msgbox.cs#6)]
 [!code-vb[Conceptual.Interop.Marshaling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/msgbox.vb#6)]  
  
## 請參閱  
 [封送處理字串](../../../docs/framework/interop/marshaling-strings.md)   
 [Platform Invoke Data Types](http://msdn.microsoft.com/zh-tw/16014d9f-d6bd-481e-83f0-df11377c550f)   
 [字串的預設封送處理](../../../docs/framework/interop/default-marshaling-for-strings.md)   
 [在 Managed 程式碼中建立原型](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)   
 [指定字元集](../../../docs/framework/interop/specifying-a-character-set.md)