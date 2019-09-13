---
title: 封送處理類別、結構和等位
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data marshaling, classes
- marshaling, unions
- marshaling, structures
- marshaling, samples
- data marshaling, structures
- platform invoke, marshaling data
- marshaling, classes
- data marshaling, unions
- data marshaling, samples
- data marshaling, platform invoke
- marshaling, platform invoke
ms.assetid: 027832a2-9b43-4fd9-9b45-7f4196261a4e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 09179ebe123f1287c8b057783bb421153f5e1183
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894176"
---
# <a name="marshaling-classes-structures-and-unions"></a>封送處理類別、結構和等位
在 .NET Framework 中，類別和結構相類似。 兩者都可以有欄位、屬性和事件。 也可以有靜態和非靜態方法。 一個值得注意的差異在於結構是實值類型，而類別是參考類型。  
  
 下表列出類別、結構和等位的封送處理選項，並描述其用法，以及提供對應平台的叫用範例連結。  
  
|類型|描述|範例|  
|----------|-----------------|------------|  
|傳值呼叫|做為 In/Out 參數，如 Managed 案例，會傳遞具有整數成員的類別。|SysTime 範例|  
|結構傳值。|傳遞結構做為 In 參數。|結構範例|  
|結構傳址。|傳遞結構做為 In/Out 參數。|OSInfo 範例|  
|具有巢狀結構 (扁平化) 的結構。|傳遞類別，表示具有 Unmanaged 函式中巢狀結構的結構。 在 Managed 原型中，結構被扁平化為一個大的結構。|FindFile 範例|  
|指標指向另一個結構的結構。|傳遞一個結構，其包含的指標指向第二個做為成員的結構。|結構範例|  
|整數傳值的結構陣列。|將僅包含整數的結構陣列做為 In/Out 參數傳遞。 可變更陣列的成員。|陣列範例|  
|整數結構和傳址字串的陣列。|傳遞包含整數和字串做為 Out 參數的結構陣列。 所呼叫的函式會配置此陣列的記憶體。|OutArrayOfStructs 範例|  
|具有實值類型的等位。|傳遞具有實值類型的等位 (整數和雙精度浮點數)。|等位範例|  
|具有混合類型的等位。|傳遞具有混合類型的等位 (整數和字串)。|等位範例|  
|在結構中的 null 值。|傳遞 Null 參考 (在 Visual Basic 中為 **Nothing**)，而非實值型別的參考。|HandleRef 範例|  
  
## <a name="structures-sample"></a>結構範例  
 這個範例示範如何傳遞指向第二個結構的結構、傳遞具有內嵌結構的結構，以及傳遞具有內嵌陣列的結構。  
  
 本結構範例會使用下列 Unmanaged 函式，和其原始函式宣告，如下所示：  
  
- 從 PinvokeLib.dll 匯出的 **TestStructInStruct**。  
  
    ```cpp  
    int TestStructInStruct(MYPERSON2* pPerson2);  
    ```  
  
- 從 PinvokeLib.dll 匯出的 **TestStructInStruct3**。  
  
    ```cpp  
    void TestStructInStruct3(MYPERSON3 person3);  
    ```  
  
- 從 PinvokeLib.dll 匯出的 **TestArrayInStruct**。  
  
    ```cpp  
    void TestArrayInStruct( MYARRAYSTRUCT* pStruct );  
    ```  
  
 [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) 是自訂的非受控程式庫，其中包含先前所列出函式和四個結構的實作：**MYPERSON**、**MYPERSON2**、**MYPERSON3** 和 **MYARRAYSTRUCT**。 這些結構包含下列項目：  
  
```cpp  
typedef struct _MYPERSON  
{  
   char* first;   
   char* last;   
} MYPERSON, *LP_MYPERSON;  
  
typedef struct _MYPERSON2  
{  
   MYPERSON* person;  
   int age;   
} MYPERSON2, *LP_MYPERSON2;  
  
typedef struct _MYPERSON3  
{  
   MYPERSON person;  
   int age;   
} MYPERSON3;  
  
typedef struct _MYARRAYSTRUCT  
{  
   bool flag;  
   int vals[ 3 ];   
} MYARRAYSTRUCT;  
```  
  
 Managed `MyPerson`、`MyPerson2`、`MyPerson3` 和 `MyArrayStruct` 結構的特性如下：  
  
- `MyPerson` 僅包含字串成員。 當傳遞給 Unmanaged 函式時，[CharSet](specifying-a-character-set.md) 欄位會將字串設定為 ANSI 格式。  
  
- `MyPerson2` 包含 `MyPerson` 結構的 **IntPtr**。 **IntPtr** 類型會取代原始指標的 Unmanaged 結構，因為 .NET Framework 應用程式不會使用指標，除非將程式碼標示為 **Unsafe**。  
  
- `MyPerson3` 包含 `MyPerson` 做為內嵌結構。 藉由將內嵌結構的項目放在主結構中，可扁平化內嵌於其它結構的結構，或者將它留下做為內嵌結構，如本範例所完成的動作。  
  
- `MyArrayStruct` 包含一個整數的陣列。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性會將 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉值設定為 **ByValArray**，用來表示陣列項目數。  
  
 對於本範例的所有結構，套用 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性來確定此成員以其顯示的順序循序排列在記憶體中。  
  
 `LibWrap` 類別包含 `TestStructInStruct`、`TestStructInStruct3` 及 `TestArrayInStruct` 方法的 Managed 原型，這些方法由 `App` 類別所呼叫。 每一個原型會宣告單一參數，如下所示：  
  
- `TestStructInStruct` 宣告一個參考給 `MyPerson2` 類型做為它的參數。  
  
- `TestStructInStruct3` 宣告 `MyPerson3` 類型做為它的參數，並以傳值方式傳遞參數。  
  
- `TestArrayInStruct` 宣告一個參考給 `MyArrayStruct` 類型做為它的參數。  
  
 除非此參數包含 **ref** 關鍵字 (在 Visual Basic 中為 **ByRef**)，否則作為方法引數的結構會以傳值方式傳遞。 例如， `TestStructInStruct` 方法會傳遞對於類型物件 `MyPerson2` 的參考 (位址的值) 給 Unmanaged 程式碼。 若要管理 `MyPerson2` 指向的結構，此範例會建立指定大小的緩衝區，並藉由合併 <xref:System.Runtime.InteropServices.Marshal.AllocCoTaskMem%2A?displayProperty=nameWithType> 和 <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> 方法，傳回其位址。 接下來，範例會將 Managed 結構的內容複製到 Unmanaged 緩衝區。 最後，此範例會使用 <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A?displayProperty=nameWithType> 方法自 Unmanaged 緩衝區封送處理資料到 Managed 物件，並以 <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A?displayProperty=nameWithType> 方法來釋放 Unmanaged 記憶體區塊。  
  
### <a name="declaring-prototypes"></a>宣告原型  
 [!code-cpp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#23)]
 [!code-csharp[Conceptual.Interop.Marshaling#23](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#23)]
 [!code-vb[Conceptual.Interop.Marshaling#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#23)]  
  
### <a name="calling-functions"></a>呼叫函式  
 [!code-cpp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/structures.cpp#24)]
 [!code-csharp[Conceptual.Interop.Marshaling#24](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/structures.cs#24)]
 [!code-vb[Conceptual.Interop.Marshaling#24](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/structures.vb#24)]  
  
## <a name="findfile-sample"></a>FindFile 範例  
 這個範例示範如何傳遞包含第二個內嵌結構的結構給 Unmanaged 函式。 它也會示範如何使用 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性在結構內宣告固定長度的陣列。 在此範例中，會加入內嵌結構項目至其父結構。 如需未扁平化內嵌結構的範例，請參閱[結構範例](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/eadtsekz(v=vs.100))。  
  
 FindFile 範例會使用下列 Unmanaged 函式，和其原始函式宣告，如下所示：  
  
- 從 Kernel32.dll 匯出 **FindFirstFile**。  
  
    ```cpp
    HANDLE FindFirstFile(LPCTSTR lpFileName, LPWIN32_FIND_DATA lpFindFileData);  
    ```  
  
 傳遞至函式的原始結構包含下列項目：  
  
```cpp
typedef struct _WIN32_FIND_DATA   
{  
  DWORD    dwFileAttributes;   
  FILETIME ftCreationTime;   
  FILETIME ftLastAccessTime;   
  FILETIME ftLastWriteTime;   
  DWORD    nFileSizeHigh;   
  DWORD    nFileSizeLow;   
  DWORD    dwReserved0;   
  DWORD    dwReserved1;   
  TCHAR    cFileName[ MAX_PATH ];   
  TCHAR    cAlternateFileName[ 14 ];   
} WIN32_FIND_DATA, *PWIN32_FIND_DATA;  
```  
  
 在此範例中， `FindData` 類別包含原始結構的每個項目所對應的資料成員和內嵌結構。 為了取代 2 個原始字元緩衝區，類別會替代字串。 **MarshalAsAttribute** 會將 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉設定為 **ByValTStr**，這用來識別出現在 Unmanaged 結構中內嵌固定長度的字元陣列。  
  
 `LibWrap` 類別包含 `FindFirstFile` 方法的 Managed 原型，會傳遞 `FindData` 類別做為參數。 參數必須以 <xref:System.Runtime.InteropServices.InAttribute> 和 <xref:System.Runtime.InteropServices.OutAttribute> 屬性宣告，因為根據預設，會傳遞參考類型的類別做為 In 參數。  
  
### <a name="declaring-prototypes"></a>宣告原型  
 [!code-cpp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#17)]
 [!code-csharp[Conceptual.Interop.Marshaling#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#17)]
 [!code-vb[Conceptual.Interop.Marshaling#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#17)]  
  
### <a name="calling-functions"></a>呼叫函式  
 [!code-cpp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/findfile.cpp#18)]
 [!code-csharp[Conceptual.Interop.Marshaling#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/findfile.cs#18)]
 [!code-vb[Conceptual.Interop.Marshaling#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/findfile.vb#18)]  
  
## <a name="unions-sample"></a>等位範例  
 這個範例示範如何傳遞結構至需要等位的 Unmanged 函式，該結構僅包含實值類型、包含實值類型的結構和一個做為參數的字串。 等位表示可由兩個或多個變數共用的記憶體位置。  
  
 Unions 範例會使用下列 Unmanaged 函式，和其原始函式宣告，如下所示：  
  
- 從 PinvokeLib.dll 匯出的 **TestUnion**。  
  
    ```cpp
    void TestUnion(MYUNION u, int type);  
    ```  
  
 [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) 是自訂的 Unmanaged 程式庫，其中包含先前所列出函式以及 **MYUNION** 和 **MYUNION2** 這兩個等位的實作。 此等位包含下列項目：  
  
```cpp
union MYUNION  
{  
    int number;  
    double d;  
}  
  
union MYUNION2  
{  
    int i;  
    char str[128];  
};  
```  
  
 在 Managed 程式碼中，會定義等位為結構。 `MyUnion` 結構包含兩個做為其成員的實值類型：整數和雙精度浮點數。 設定 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性來控制每個資料成員的精確位置。 <xref:System.Runtime.InteropServices.FieldOffsetAttribute> 屬性會提供等位的 Unmanaged 表示中的欄位實體位置。 請注意這兩個成員具有相同的位移值，所以成員可以定義相同的記憶體。  
  
 `MyUnion2_1` 和 `MyUnion2_2` 分別包含實值類型 (整數) 和字串。 在 Managed 程式碼中，實值類型及參考類型不允許重疊。 此範例會使用方法多載化來讓呼叫端在呼叫相同 Unmanaged 函式時使用這兩種類型。 `MyUnion2_1` 配置則是明確的，且具有精確位移值。 相反地，`MyUnion2_2` 具有循序配置，因為對參考類型不允許明確的配置。 <xref:System.Runtime.InteropServices.MarshalAsAttribute> 屬性會將 <xref:System.Runtime.InteropServices.UnmanagedType> 列舉設定為 **ByValTStr**，這用來識別出現在該等位的 Unmanaged 表示中內嵌固定長度的字元陣列。  
  
 `LibWrap` 類別包含 `TestUnion` 和 `TestUnion2` 方法的原型。 `TestUnion2` 被多載，以宣告 `MyUnion2_1` 或 `MyUnion2_2` 做為參數。  
  
### <a name="declaring-prototypes"></a>宣告原型  
 [!code-cpp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#28)]
 [!code-csharp[Conceptual.Interop.Marshaling#28](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#28)]
 [!code-vb[Conceptual.Interop.Marshaling#28](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#28)]  
  
### <a name="calling-functions"></a>呼叫函式  
 [!code-cpp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/unions.cpp#29)]
 [!code-csharp[Conceptual.Interop.Marshaling#29](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/unions.cs#29)]
 [!code-vb[Conceptual.Interop.Marshaling#29](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/unions.vb#29)]  
  
## <a name="systime-sample"></a>SysTime 範例  
 這個範例示範如何將指向類別的指標傳遞至需要指向結構指標的 Unmanaged 函式。  
  
 SysTime 範例會使用下列 Unmanaged 函式，和其原始函式宣告，如下所示：  
  
- 從 Kernel32.dll 匯出 **GetSystemTime**。  
  
    ```cpp
    VOID GetSystemTime(LPSYSTEMTIME lpSystemTime);  
    ```  
  
 傳遞至函式的原始結構包含下列項目：  
  
```cpp
typedef struct _SYSTEMTIME {   
    WORD wYear;   
    WORD wMonth;   
    WORD wDayOfWeek;   
    WORD wDay;   
    WORD wHour;   
    WORD wMinute;   
    WORD wSecond;   
    WORD wMilliseconds;   
} SYSTEMTIME, *PSYSTEMTIME;  
```  
  
 在此範例中，`SystemTime` 類別包含表示為類別成員原始結構的項目。 已設定 <xref:System.Runtime.InteropServices.StructLayoutAttribute> 屬性來確定此成員以其顯示的順序循序排列在記憶體中。  
  
 `LibWrap` 類別包含 `GetSystemTime` 方法的 Managed 原型，根據預設會傳遞 `SystemTime` 類別做為 In/Out 參數。 參數必須以 <xref:System.Runtime.InteropServices.InAttribute> 和 <xref:System.Runtime.InteropServices.OutAttribute> 屬性宣告，因為根據預設，會傳遞參考類型的類別做為 In 參數。 若要讓呼叫端接收結果，則必須明確地套用這些[方向屬性](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))。 `App` 類別建立 `SystemTime` 類別的新執行個體，並存取其資料欄位。  
  
### <a name="code-samples"></a>程式碼範例  
 [!code-cpp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/systime.cpp#25)]
 [!code-csharp[Conceptual.Interop.Marshaling#25](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/systime.cs#25)]
 [!code-vb[Conceptual.Interop.Marshaling#25](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/systime.vb#25)]  
  
## <a name="outarrayofstructs-sample"></a>OutArrayOfStructs 範例  
 這個範例顯示如何傳遞包含整數和字串做為 Out 參數的結構陣列至 Unmanaged 函式。  
  
 這個範例示範如何藉由使用 <xref:System.Runtime.InteropServices.Marshal> 類別和使用 Unsafe 程式碼來呼叫原生函式。  
  
 這個範例使用定義在 [PinvokeLib.dll](marshaling-data-with-platform-invoke.md#pinvokelibdll) 中的包裝函式和平台叫用，這些也在原始程式檔中提供。 它會使用 `TestOutArrayOfStructs` 函式和 `MYSTRSTRUCT2` 結構。 此結構包含下列項目：  
  
```cpp
typedef struct _MYSTRSTRUCT2  
{  
   char* buffer;  
   UINT size;   
} MYSTRSTRUCT2;  
```  
  
 `MyStruct` 類別包含 ANSI 字元的字串物件。 <xref:System.Runtime.InteropServices.DllImportAttribute.CharSet> 欄位指定 ANSI 格式。 `MyUnsafeStruct` 為包含 <xref:System.IntPtr> 類型的結構，而非字串。  
  
 `LibWrap` 類別包含 `TestOutArrayOfStructs` 多載原型方法。 如果方法宣告指標做為參數，此類別會以 `unsafe` 關鍵字標記。 因為 Visual Basic 不能使用不安全的程式碼，所以多載的方法、Unsafe 修飾詞和 `MyUnsafeStruct` 結構是不必要的。  
  
 `App` 類別會實作 `UsingMarshaling` 方法，該方法會執行所有用來傳遞陣列的必要工作。 該陣列以 `out` (在 Visual Basic 中為`ByRef`) 關鍵字標記，表示該資料從被呼叫端傳遞至呼叫端。 此實作會使用下列 <xref:System.Runtime.InteropServices.Marshal> 類別方法：  
  
- <xref:System.Runtime.InteropServices.Marshal.PtrToStructure%2A> 從 Unmanaged 緩衝區封送處理資料至 Managed 物件。  
  
- <xref:System.Runtime.InteropServices.Marshal.DestroyStructure%2A> 用來釋放在結構中為字串保留的記憶體。  
  
- <xref:System.Runtime.InteropServices.Marshal.FreeCoTaskMem%2A> 用來釋放為陣列保留的記憶體。  
  
 如先前所述，C# 允許不安全的程式碼，而 Visual Basic 則否。 在 C# 範例中， `UsingUnsafePointer` 是一種替代的方法實作，會使用指標，而非 <xref:System.Runtime.InteropServices.Marshal> 類別，以傳回包含 `MyUnsafeStruct` 結構的陣列。  
  
### <a name="declaring-prototypes"></a>宣告原型  
 [!code-cpp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#20)]
 [!code-csharp[Conceptual.Interop.Marshaling#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#20)]
 [!code-vb[Conceptual.Interop.Marshaling#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#20)]  
  
### <a name="calling-functions"></a>呼叫函式  
 [!code-cpp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.interop.marshaling/cpp/outarrayofstructs.cpp#21)]
 [!code-csharp[Conceptual.Interop.Marshaling#21](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.interop.marshaling/cs/outarrayofstructs.cs#21)]
 [!code-vb[Conceptual.Interop.Marshaling#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.interop.marshaling/vb/outarrayofstructs.vb#21)]  
  
## <a name="see-also"></a>另請參閱

- [使用平台叫用封送處理資料](marshaling-data-with-platform-invoke.md)
- [封送處理字串](marshaling-strings.md)
- [封送處理不同類型的陣列](marshaling-different-types-of-arrays.md)
