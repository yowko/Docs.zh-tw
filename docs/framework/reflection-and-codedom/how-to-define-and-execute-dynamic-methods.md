---
title: "如何：定義和執行動態方法"
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
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7c2b3f1707aab1f83d8f8c6a06bc2efa909134d5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-define-and-execute-dynamic-methods"></a>如何：定義和執行動態方法
下列程序顯示如何定義及執行簡單的動態方法及繫結至類別執行個體的動態方法。 如需動態方法的詳細資訊，請參閱 <xref:System.Reflection.Emit.DynamicMethod> 類別和[反映發出動態方法案例](http://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)。  
  
### <a name="to-define-and-execute-a-dynamic-method"></a>定義和執行動態方法  
  
1.  宣告委派類型來執行方法。 請考慮使用泛型委派，將您需要宣告的委派類型數目降到最低。 下列程式碼會宣告兩個可用於 `SquareIt` 方法的委派類型，其中之一是泛型。  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  建立陣列，指定動態方法的參數類型。 在此範例中，唯一的參數是 `int` (Visual Basic 為 `Integer`)，所以陣列只有一個項目。  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  建立 <xref:System.Reflection.Emit.DynamicMethod>。 本例中的方法名為 `SquareIt`。  
  
    > [!NOTE]
    >  不需要提供動態方法名稱，它們無法依名稱叫用。 多個動態方法可有相同的名稱。 不過，名稱會出現在呼叫堆疊中，有利於偵錯。  
  
     傳回值的類型指定為 `long`。 與包含 `Example` 類別的模組建立關聯的方法，包含範例程式碼。 可指定任何已載入的模組。 動態方法的行為如同模組層級的 `static` 方法 (Visual Basic 為 `Shared`)。  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  發出方法主體。 本例中使用 <xref:System.Reflection.Emit.ILGenerator> 物件發出 Microsoft 中繼語言 (MSIL)。 或者，您可使用 <xref:System.Reflection.Emit.DynamicILInfo> 物件結合 Unmanaged 程式碼產生器，發出 <xref:System.Reflection.Emit.DynamicMethod> 的方法主體。  
  
     本例中的 MSIL 是 `int`，會將引數載入到堆疊上，再將它轉換成 `long`，重複 `long` 再將兩個數字相乘。 這會將平方的結果留在堆疊上，而方法唯一要做的只有傳回。  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  呼叫 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> 方法，以建立表示動態方法之 (在步驟 1 中宣告) 委派的執行個體。 建立委派即會完成方法，而任何進一步變更方法的嘗試，例如新增更多的 MSIL，則予以忽略。 下列程式碼會使用泛型委派，建立並叫用委派。  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### <a name="to-define-and-execute-a-dynamic-method-that-is-bound-to-an-object"></a>定義及執行繫結至物件的動態方法  
  
1.  宣告委派類型來執行方法。 請考慮使用泛型委派，將您需要宣告的委派類型數目降到最低。 下列程式碼會宣告泛型委派類型，其可用於執行任何具有一個參數和傳回值的方法，如果委派繫結至物件，則可為具有兩個參數和傳回值的方法。  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  建立陣列，指定動態方法的參數類型。 如果表示方法的委派繫結至物件，第一個參數就必須符合委派繫結的類型。 本例中有兩個參數，類型 `Example` 和類型 `int` (Visual Basic 為 `Integer`)。  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  建立 <xref:System.Reflection.Emit.DynamicMethod>。 本例中的方法沒有名稱。 傳回值的類型指定為 `int` (Visual Basic 為 `Integer`)。 方法可以存取 `Example` 類別的私用和受保護成員。  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  發出方法主體。 本例中使用 <xref:System.Reflection.Emit.ILGenerator> 物件發出 Microsoft 中繼語言 (MSIL)。 或者，您可使用 <xref:System.Reflection.Emit.DynamicILInfo> 物件結合 Unmanaged 程式碼產生器，發出 <xref:System.Reflection.Emit.DynamicMethod> 的方法主體。  
  
     本例中的 MSIL 是 `Example` 類別的執行個體，它會載入第一個引數，再使用它載入類型 `int` 的私用執行個體欄位值。 載入第二個引數，然後兩個數字相乘。 如果結果大於 `int`，則截斷值，捨棄最高有效位元。 方法傳回，附有堆疊上的傳回值。  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  呼叫 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> 方法多載，以建立表示動態方法之 (步驟 1 所宣告的) 委派的執行個體。 建立委派即會完成方法，而任何進一步變更方法的嘗試，例如新增更多的 MSIL，則予以忽略。  
  
    > [!NOTE]
    >  您可以多次呼叫 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> 方法，建立繫結至其他目標類型執行個體的委派。  
  
     下列程式碼會將方法繫結至 `Example` 類別的新執行個體，此類別的私用測試欄位設為 42。 亦即，每次叫用委派時，`Example` 的執行個體都會傳遞至方法的第一個參數。  
  
     因為方法的第一個參數一律會收到 `Example` 的執行個體，所以使用委派 `OneParameter`。 叫用委派時，只需要第二個參數。  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## <a name="example"></a>範例  
 下列程式碼範例會示範簡單的動態方法及繫結至類別執行個體的動態方法。  
  
 簡單的動態方法接受一個 32 位元整數的引數，並傳回該整數的 64 位元平方。 使用泛型委派叫用方法。  
  
 第二個動態方法有兩個參數，類型 `Example` 和類型 `int` (Visual Basic 為 `Integer`)。 動態方法建立後，會使用有一個類別 `int` 引數的泛型委派，繫結至 `Example` 的執行個體。 因為方法的第一個參數一律會收到 `Example` 的繫結執行個體，所以委派沒有類型 `Example` 的引數。 叫用委派時，只提供 `int` 引數。 此動態方法會存取 `Example` 類別的私用欄位，並傳回私用欄位和 `int` 引數的乘積。  
  
 程式碼範例會定義委派，此委派可用以執行方法。  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
  
-   此程式碼包含編譯所需的 C# `using` 陳述式 (Visual Basic 為 `Imports`)。  
  
-   不需要任何其他組件參考。  
  
-   在命令列使用 csc.exe、vbc.exe 或 cl.exe 編譯程式碼。 若要編譯 Visual Studio 中的程式碼，請將它放在主控台應用程式專案範本。  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Reflection.Emit.DynamicMethod>  
 [使用反映發出](http://msdn.microsoft.com/library/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [反映發出動態方法案例](http://msdn.microsoft.com/library/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)
