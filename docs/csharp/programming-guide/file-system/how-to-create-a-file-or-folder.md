---
title: 作法：建立檔案或資料夾 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- folders [C#]
- creating files [C#]
- files [C#]
- creating folders [C#]
ms.assetid: 4582ee2d-d72d-4687-bcb9-08d336c62c25
ms.openlocfilehash: 3163598de5d03bf1691379cddae031841b9865d6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595645"
---
# <a name="how-to-create-a-file-or-folder-c-programming-guide"></a><span data-ttu-id="b44a8-102">作法：建立檔案或資料夾 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b44a8-102">How to: Create a File or Folder (C# Programming Guide)</span></span>
<span data-ttu-id="b44a8-103">您可以程式設計的方式在電腦上建立資料夾、建立子資料夾、在子資料夾中建立檔案，以及將資料寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="b44a8-103">You can programmatically create a folder on your computer, create a subfolder, create a file in the subfolder, and write data to the file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b44a8-104">範例</span><span class="sxs-lookup"><span data-stu-id="b44a8-104">Example</span></span>  
 [!code-csharp[csFilesandFolders#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csFilesAndFolders/CS/FileIteration.cs#10)]  
  
 <span data-ttu-id="b44a8-105">若資料夾已經存在，<xref:System.IO.Directory.CreateDirectory%2A> 不會採取任何動作，也不會擲回任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b44a8-105">If the folder already exists, <xref:System.IO.Directory.CreateDirectory%2A> does nothing, and no exception is thrown.</span></span> <span data-ttu-id="b44a8-106">但 <xref:System.IO.File.Create%2A?displayProperty=nameWithType> 會以新的檔案取代現有的檔案。</span><span class="sxs-lookup"><span data-stu-id="b44a8-106">However, <xref:System.IO.File.Create%2A?displayProperty=nameWithType> replaces an existing file with a new file.</span></span> <span data-ttu-id="b44a8-107">此例使用 `if` - `else` 陳述式防止現有的檔案被取代。</span><span class="sxs-lookup"><span data-stu-id="b44a8-107">The example uses an `if`-`else` statement to prevent an existing file from being replaced.</span></span>  
  
 <span data-ttu-id="b44a8-108">透過在範例中進行下列變更，您可以根據是否已有具特定名稱的檔案來指定不同的結果。</span><span class="sxs-lookup"><span data-stu-id="b44a8-108">By making the following changes in the example, you can specify different outcomes based on whether a file with a certain name already exists.</span></span> <span data-ttu-id="b44a8-109">如果沒有這類檔案，程式碼會建立一個。</span><span class="sxs-lookup"><span data-stu-id="b44a8-109">If such a file doesn't exist, the code creates one.</span></span> <span data-ttu-id="b44a8-110">如果有這類檔案，程式碼會將資料附加至該檔案。</span><span class="sxs-lookup"><span data-stu-id="b44a8-110">If such a file exists, the code appends data to that file.</span></span>  
  
- <span data-ttu-id="b44a8-111">指定非隨機的檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="b44a8-111">Specify a non-random file name.</span></span>  
  
    ```csharp  
    // Comment out the following line.  
    //string fileName = System.IO.Path.GetRandomFileName();  
  
    // Replace that line with the following assignment.  
    string fileName = "MyNewFile.txt";  
    ```  
  
- <span data-ttu-id="b44a8-112">請在下列程式碼中以 `using` 陳述式取代 `if`-`else` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b44a8-112">Replace the `if`-`else` statement with the `using` statement in the following code.</span></span>  
  
    ```csharp  
    using (System.IO.FileStream fs = new System.IO.FileStream(pathString, FileMode.Append))   
    {  
        for (byte i = 0; i < 100; i++)  
        {  
            fs.WriteByte(i);  
        }  
    }  
    ```  
  
 <span data-ttu-id="b44a8-113">執行數次範例以確認資料是否每次都新增至檔案。</span><span class="sxs-lookup"><span data-stu-id="b44a8-113">Run the example several times to verify that data is added to the file each time.</span></span>  
  
 <span data-ttu-id="b44a8-114">若要取得更多可以嘗試的 `FileMode` 值，請參考 <xref:System.IO.FileMode>。</span><span class="sxs-lookup"><span data-stu-id="b44a8-114">For more `FileMode` values that you can try, see <xref:System.IO.FileMode>.</span></span>  
  
 <span data-ttu-id="b44a8-115">以下條件可能會造成例外狀況：</span><span class="sxs-lookup"><span data-stu-id="b44a8-115">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="b44a8-116">資料夾名稱的格式不正確。</span><span class="sxs-lookup"><span data-stu-id="b44a8-116">The folder name is malformed.</span></span> <span data-ttu-id="b44a8-117">舉例來說，其可能包含非法的字元，或是只有空白字元 (<xref:System.ArgumentException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="b44a8-117">For example, it contains illegal characters or is only white space (<xref:System.ArgumentException> class).</span></span> <span data-ttu-id="b44a8-118">請使用 <xref:System.IO.Path> 類別建立有效的路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="b44a8-118">Use the <xref:System.IO.Path> class to create valid path names.</span></span>  
  
- <span data-ttu-id="b44a8-119">要建立之資料夾的父資料夾為唯讀 (<xref:System.IO.IOException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="b44a8-119">The parent folder of the folder to be created is read-only (<xref:System.IO.IOException> class).</span></span>  
  
- <span data-ttu-id="b44a8-120">資料夾名稱為 `null` (<xref:System.ArgumentNullException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="b44a8-120">The folder name is `null` (<xref:System.ArgumentNullException> class).</span></span>  
  
- <span data-ttu-id="b44a8-121">資料夾名稱過長 (<xref:System.IO.PathTooLongException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="b44a8-121">The folder name is too long (<xref:System.IO.PathTooLongException> class).</span></span>  
  
- <span data-ttu-id="b44a8-122">資料夾名稱只是一個冒號 ":" (<xref:System.IO.PathTooLongException> 類別)。</span><span class="sxs-lookup"><span data-stu-id="b44a8-122">The folder name is only a colon, ":" (<xref:System.IO.PathTooLongException> class).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="b44a8-123">.NET Framework 安全性</span><span class="sxs-lookup"><span data-stu-id="b44a8-123">.NET Framework Security</span></span>  
 <span data-ttu-id="b44a8-124">在部分信任的狀況下，可能會擲回 <xref:System.Security.SecurityException> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b44a8-124">An instance of the <xref:System.Security.SecurityException> class may be thrown in partial-trust situations.</span></span>  
  
 <span data-ttu-id="b44a8-125">若您沒有權限可建立資料夾，則範例會擲回 <xref:System.UnauthorizedAccessException> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b44a8-125">If you don’t have permission to create the folder, the example throws an instance of the <xref:System.UnauthorizedAccessException> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b44a8-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b44a8-126">See also</span></span>

- <xref:System.IO?displayProperty=nameWithType>
- [<span data-ttu-id="b44a8-127">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b44a8-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="b44a8-128">檔案系統和登錄 (C# 程式設計指南)</span><span class="sxs-lookup"><span data-stu-id="b44a8-128">File System and the Registry (C# Programming Guide)</span></span>](../../../csharp/programming-guide/file-system/index.md)
