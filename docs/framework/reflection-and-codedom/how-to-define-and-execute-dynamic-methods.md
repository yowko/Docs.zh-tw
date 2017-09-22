---
title: "如何：定義和執行動態方法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- reflection emit, dynamic methods
- dynamic methods
ms.assetid: 07d08a99-62c5-4254-bce2-2a75e55a18ab
caps.latest.revision: 12
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 67e909a7b64500bba533290061652e82ffde07a5
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# 如何：定義和執行動態方法
下列程序將示範如何定義及執行簡單的動態方法及繫結至類別執行個體的動態方法。  如需動態方法的詳細資訊，請參閱 <xref:System.Reflection.Emit.DynamicMethod> 類別和[Reflection Emit Dynamic Method Scenarios](http://msdn.microsoft.com/zh-tw/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)。  
  
### 若要定義及執行動態方法  
  
1.  宣告委派型別來執行此方法。  請考慮使用泛型委派，將您需要宣告的委派型別數目減至最少。  下列程式碼將宣告兩個可用於 `SquareIt` 方法的委派型別，而其中一個是泛型。  
  
     [!code-cpp[DynamicMethodHowTo#2](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#2)]
     [!code-csharp[DynamicMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#2)]
     [!code-vb[DynamicMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#2)]  
  
2.  建立一個陣列，此陣列可為動態方法指定參數型別。  在此範例中，唯一的參數是 `int` \(Visual Basic 中為 `Integer`\)，所以此陣列只有一個元素。  
  
     [!code-cpp[DynamicMethodHowTo#3](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#3)]
     [!code-csharp[DynamicMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#3)]
     [!code-vb[DynamicMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#3)]  
  
3.  建立 <xref:System.Reflection.Emit.DynamicMethod>。  在此範例中，此方法命名為 `SquareIt`。  
  
    > [!NOTE]
    >  不需要提供動態方法名稱，也不能根據名稱來叫用這些方法。  可以讓多個動態方法有相同的名稱；  但是，此名稱會出現在呼叫堆疊中，且對於偵錯可能很有用處。  
  
     傳回值的型別會指定為 `long`。  此方法會與包含 `Example` 類別的模組產生關聯，而此類別包含了範例程式碼；  任何載入的模組都可以指定。  動態方法的運作方式就像是模組層級的 `static` 方法 \(Visual Basic 中為 `Shared`\)。  
  
     [!code-cpp[DynamicMethodHowTo#4](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#4)]
     [!code-csharp[DynamicMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#4)]
     [!code-vb[DynamicMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#4)]  
  
4.  發出方法主體。  在此範例中，會使用 <xref:System.Reflection.Emit.ILGenerator> 物件來發出 Microsoft intermediate language \(MSIL\)。  另外，也可以將 <xref:System.Reflection.Emit.DynamicILInfo> 物件搭配 Unmanaged 程式碼產生器一起使用，以發出 <xref:System.Reflection.Emit.DynamicMethod> 的方法主體。  
  
     此範例中的 MSIL 會將引數 \(亦即 `int`\) 載入到堆疊上、將它轉換成 `long`、複製 `long`，並將這兩個數字相乘。  如此會讓相乘的結果留在堆疊上，而所有方法必須做的事情就是傳回。  
  
     [!code-cpp[DynamicMethodHowTo#5](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#5)]
     [!code-csharp[DynamicMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#5)]
     [!code-vb[DynamicMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#5)]  
  
5.  藉由呼叫 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> 方法來建立委派的執行個體 \(步驟 1 中所宣告\)，其表示動態方法。  建立此委派即會完成此方法，而任何進一步嘗試變更此方法的動作 \(例如，加入更多的 MSIL\) 都會被忽略。  下列程式碼會使用泛型委派，以建立委派並叫用它。  
  
     [!code-cpp[DynamicMethodHowTo#6](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#6)]
     [!code-csharp[DynamicMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#6)]
     [!code-vb[DynamicMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#6)]  
  
### 若要定義及執行繫結至物件的動態方法  
  
1.  宣告委派型別來執行此方法。  請考慮使用泛型委派，將您需要宣告的委派型別數目減至最少。  下列程式碼會宣告可用來執行任何具有一個參數和一個傳回值的方法之泛型委派型別；如果此委派繫結至物件，則為具有兩個參數和一個傳回值的方法。  
  
     [!code-cpp[DynamicMethodHowTo#12](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#12)]
     [!code-csharp[DynamicMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#12)]
     [!code-vb[DynamicMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#12)]  
  
2.  建立一個陣列，此陣列可為動態方法指定參數型別。  如果表示此方法的委派要繫結至物件，則第一個參數必須符合此委派所繫結的型別。  此範例中有兩個參數，其型別為 `Example` 和型別 `int` \(Visual Basic 中為 `Integer`\)。  
  
     [!code-cpp[DynamicMethodHowTo#13](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#13)]
     [!code-csharp[DynamicMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#13)]
     [!code-vb[DynamicMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#13)]  
  
3.  建立 <xref:System.Reflection.Emit.DynamicMethod>。  在此範例中，此方法沒有名稱。  傳回值的型別會指定為 `int` \(Visual Basic 中為 `Integer`\)。  此方法對於 `Example` 類別的私用和受保護的成員具有存取權。  
  
     [!code-cpp[DynamicMethodHowTo#14](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#14)]
     [!code-csharp[DynamicMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#14)]
     [!code-vb[DynamicMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#14)]  
  
4.  發出方法主體。  在此範例中，會使用 <xref:System.Reflection.Emit.ILGenerator> 物件來發出 Microsoft intermediate language \(MSIL\)。  另外，也可以將 <xref:System.Reflection.Emit.DynamicILInfo> 物件搭配 Unmanaged 程式碼產生器一起使用，以發出 <xref:System.Reflection.Emit.DynamicMethod> 的方法主體。  
  
     此範例中的 MSIL 會載入第一個引數 \(此引數為 `Example` 類別的執行個體\)，並使用它來載入型別為 `int` 的私用執行個體欄位的值。  第二個引數也會載入，而這兩個數字會相乘。  如果相乘結果大於 `int`，則這個值會被截斷，且會捨棄最明顯的位元。  然後此方法會傳回，且包含堆疊上的傳回值。  
  
     [!code-cpp[DynamicMethodHowTo#15](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#15)]
     [!code-csharp[DynamicMethodHowTo#15](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#15)]
     [!code-vb[DynamicMethodHowTo#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#15)]  
  
5.  藉由呼叫 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%28System.Type%2CSystem.Object%29> 方法多載來建立委派的執行個體 \(步驟 1 中所宣告\)，其表示動態方法。  建立此委派即會完成此方法，而任何進一步嘗試變更此方法的動作 \(例如，加入更多的 MSIL\) 都會被忽略。  
  
    > [!NOTE]
    >  您可以呼叫 <xref:System.Reflection.Emit.DynamicMethod.CreateDelegate%2A> 方法多次，以建立繫結至其他目標型別執行個體的委派。  
  
     下列程式碼會將此方法繫結至 `Example` 類別的新執行個體，而此類別的私用測試欄位設定為 42；  也就是說，每當叫用此委派時 `Example` 的執行個體即會傳遞給此方法的第一個參數。  
  
     會使用委派 `OneParameter`，因為此方法的第一個參數一定會收到 `Example` 的執行個體。  當叫用此委派時，只需要第二個參數。  
  
     [!code-cpp[DynamicMethodHowTo#16](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#16)]
     [!code-csharp[DynamicMethodHowTo#16](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#16)]
     [!code-vb[DynamicMethodHowTo#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#16)]  
  
## 範例  
 下列程式碼範例將示範簡單的動態方法，以及繫結至類別執行個體的動態方法。  
  
 此簡單的動態方法會接受一個引數 \(亦即 32 位元整數\)，並傳回該整數的 64 位元平方；  會使用泛型委派來叫用此方法。  
  
 第二個動態方法有兩個參數，其型別為 `Example` 和型別 `int` \(Visual Basic 中為 `Integer`\)。  當建立此動態方法時，它會繫結至 `Example` 的執行個體，其方式是使用具有一個型別為 `int` 的引數之泛型委派。  此委派沒有型別 `Example` 的引數，因為此方法的第一個參數一定會收到 `Example` 的繫結執行個體。  當叫用此委派時，只會提供 `int` 引數。  這個動態方法會存取 `Example` 類別的私用欄位，並傳回此私用欄位和 `int` 引數的乘積。  
  
 此程式碼範例會定義可用來執行方法的委派。  
  
 [!code-cpp[DynamicMethodHowTo#1](../../../samples/snippets/cpp/VS_Snippets_CLR/DynamicMethodHowTo/cpp/source.cpp#1)]
 [!code-csharp[DynamicMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/DynamicMethodHowTo/cs/source.cs#1)]
 [!code-vb[DynamicMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/DynamicMethodHowTo/vb/source.vb#1)]  
  
## 編譯程式碼  
  
-   此程式碼含有進行編譯所需的 C\# `using` 陳述式 \(Visual Basic 中的 `Imports`\)。  
  
-   不需要其他的組件參考。  
  
-   使用 csc.exe、vbc.exe 或 cl.exe 在命令列編譯程式碼。  若要在 Visual Studio 中編譯程式碼，請將程式碼放在主控台應用程式專案範本中。  
  
## 請參閱  
 <xref:System.Reflection.Emit.DynamicMethod>   
 [使用反映發出](http://msdn.microsoft.com/en-us/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)   
 [反映發出動態方法案例](http://msdn.microsoft.com/en-us/7c27ea3d-0f24-4bf3-8ceb-f49d33faca5e)

