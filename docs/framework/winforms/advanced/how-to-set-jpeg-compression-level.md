---
title: HOW TO：設定 JPEG 壓縮層級
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], changing encoder parameters
- JPEG images [Windows Forms], setting quality level
ms.assetid: 4b9a74e3-9504-43c1-9f28-ace651d0772e
ms.openlocfilehash: 1b325c0cb8fe9da4b198d19164c73af9b1609973
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626142"
---
# <a name="how-to-set-jpeg-compression-level"></a><span data-ttu-id="b9599-102">HOW TO：設定 JPEG 壓縮層級</span><span class="sxs-lookup"><span data-stu-id="b9599-102">How to: Set JPEG Compression Level</span></span>
<span data-ttu-id="b9599-103">當您將影像儲存至磁碟以減少檔案大小或改善其品質時，可能會想要修改影像的參數。</span><span class="sxs-lookup"><span data-stu-id="b9599-103">You may want to modify the parameters of an image when you save the image to disk to minimize the file size or improve its quality.</span></span> <span data-ttu-id="b9599-104">您可以修改其壓縮層級來調整 JPEG 影像的品質。</span><span class="sxs-lookup"><span data-stu-id="b9599-104">You can adjust the quality of a JPEG image by modifying its compression level.</span></span> <span data-ttu-id="b9599-105">若要儲存 JPEG 影像時，請指定的壓縮層級，您必須建立<xref:System.Drawing.Imaging.EncoderParameters>物件，並將它傳遞給<xref:System.Drawing.Image.Save%2A>方法<xref:System.Drawing.Image>類別。</span><span class="sxs-lookup"><span data-stu-id="b9599-105">To specify the compression level when you save a JPEG image, you must create an <xref:System.Drawing.Imaging.EncoderParameters> object and pass it to the <xref:System.Drawing.Image.Save%2A> method of the <xref:System.Drawing.Image> class.</span></span> <span data-ttu-id="b9599-106">初始化<xref:System.Drawing.Imaging.EncoderParameters>物件，使其具有陣列，其中包含一個<xref:System.Drawing.Imaging.EncoderParameter>。</span><span class="sxs-lookup"><span data-stu-id="b9599-106">Initialize the <xref:System.Drawing.Imaging.EncoderParameters> object so that it has an array that consists of one <xref:System.Drawing.Imaging.EncoderParameter>.</span></span> <span data-ttu-id="b9599-107">當您建立<xref:System.Drawing.Imaging.EncoderParameter>，指定<xref:System.Drawing.Imaging.Encoder.Quality>編碼器，以及所要的壓縮層級。</span><span class="sxs-lookup"><span data-stu-id="b9599-107">When you create the <xref:System.Drawing.Imaging.EncoderParameter>, specify the <xref:System.Drawing.Imaging.Encoder.Quality> encoder, and the desired compression level.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9599-108">範例</span><span class="sxs-lookup"><span data-stu-id="b9599-108">Example</span></span>  
 <span data-ttu-id="b9599-109">下列範例程式碼會建立<xref:System.Drawing.Imaging.EncoderParameter>物件，並儲存三個 JPEG 影像。</span><span class="sxs-lookup"><span data-stu-id="b9599-109">The following example code creates an <xref:System.Drawing.Imaging.EncoderParameter> object and saves three JPEG images.</span></span> <span data-ttu-id="b9599-110">每個 JPEG 影像時，會儲存使用不同的品質層級上，藉由修改`long`值傳遞至<xref:System.Drawing.Imaging.EncoderParameter>建構函式。</span><span class="sxs-lookup"><span data-stu-id="b9599-110">Each JPEG image is saved with a different quality level, by modifying the `long` value passed to the <xref:System.Drawing.Imaging.EncoderParameter> constructor.</span></span> <span data-ttu-id="b9599-111">品質層級 0 對應到最大壓縮，而品質層級 100 對應到最小壓縮。</span><span class="sxs-lookup"><span data-stu-id="b9599-111">A quality level of 0 corresponds to the greatest compression, and a quality level of 100 corresponds to the least compression.</span></span>  
  
```csharp  
private void VaryQualityLevel()  
    {  
        // Get a bitmap. The using statement ensures objects  
        // are automatically disposed from memory after use.  
        using (Bitmap bmp1 = new Bitmap(@"C:\TestPhoto.jpg"))  
        {  
            ImageCodecInfo jpgEncoder = GetEncoder(ImageFormat.Jpeg);  
  
            // Create an Encoder object based on the GUID  
            // for the Quality parameter category.  
            System.Drawing.Imaging.Encoder myEncoder =  
                System.Drawing.Imaging.Encoder.Quality;  
  
            // Create an EncoderParameters object.  
            // An EncoderParameters object has an array of EncoderParameter  
            // objects. In this case, there is only one  
            // EncoderParameter object in the array.  
            EncoderParameters myEncoderParameters = new EncoderParameters(1);  
  
            EncoderParameter myEncoderParameter = new EncoderParameter(myEncoder, 50L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"c:\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters);  
  
            myEncoderParameter = new EncoderParameter(myEncoder, 100L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters);  
  
            // Save the bitmap as a JPG file with zero quality level compression.  
            myEncoderParameter = new EncoderParameter(myEncoder, 0L);  
            myEncoderParameters.Param[0] = myEncoderParameter;  
            bmp1.Save(@"C:\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters);  
        }  
    }  
```  
  
```vb  
Private Sub VaryQualityLevel()  
    ' Get a bitmap. The Using statement ensures objects  
    ' are automatically disposed from memory after use.  
    Using bmp1 As New Bitmap("C:\test\TestPhoto.jpg")  
        Dim jpgEncoder As ImageCodecInfo = GetEncoder(ImageFormat.Jpeg)  
  
        ' Create an Encoder object based on the GUID  
        ' for the Quality parameter category.  
        Dim myEncoder As System.Drawing.Imaging.Encoder = System.Drawing.Imaging.Encoder.Quality  
  
        ' Create an EncoderParameters object.  
        ' An EncoderParameters object has an array of EncoderParameter  
        ' objects. In this case, there is only one  
        ' EncoderParameter object in the array.  
        Dim myEncoderParameters As New EncoderParameters(1)  
  
        Dim myEncoderParameter As New EncoderParameter(myEncoder, 50L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("c:\test\TestPhotoQualityFifty.jpg", jpgEncoder, myEncoderParameters)  
  
        myEncoderParameter = New EncoderParameter(myEncoder, 100L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityHundred.jpg", jpgEncoder, myEncoderParameters)  
  
        ' Save the bitmap as a JPG file with zero quality level compression.  
        myEncoderParameter = New EncoderParameter(myEncoder, 0L)  
        myEncoderParameters.Param(0) = myEncoderParameter  
        bmp1.Save("C:\test\TestPhotoQualityZero.jpg", jpgEncoder, myEncoderParameters)  
    End Using  
End Sub  
```  
  
```csharp  
private ImageCodecInfo GetEncoder(ImageFormat format)  
{  
    ImageCodecInfo[] codecs = ImageCodecInfo.GetImageDecoders();  
    foreach (ImageCodecInfo codec in codecs)  
    {  
        if (codec.FormatID == format.Guid)  
        {  
            return codec;  
        }  
    }  
    return null;  
}  
```  
  
```vb  
Private Function GetEncoder(ByVal format As ImageFormat) As ImageCodecInfo  
  
    Dim codecs As ImageCodecInfo() = ImageCodecInfo.GetImageDecoders()  
    Dim codec As ImageCodecInfo  
    For Each codec In codecs  
        If codec.FormatID = format.Guid Then  
            Return codec  
        End If  
    Next codec  
    Return Nothing  
  
End Function  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b9599-112">編譯程式碼</span><span class="sxs-lookup"><span data-stu-id="b9599-112">Compiling the Code</span></span>  
 <span data-ttu-id="b9599-113">這個範例需要：</span><span class="sxs-lookup"><span data-stu-id="b9599-113">This example requires:</span></span>  
  
- <span data-ttu-id="b9599-114">Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b9599-114">A Windows Forms application.</span></span>  
  
- <span data-ttu-id="b9599-115">A <xref:System.Windows.Forms.PaintEventArgs>，這是參數的<xref:System.Windows.Forms.PaintEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="b9599-115">A <xref:System.Windows.Forms.PaintEventArgs>, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
- <span data-ttu-id="b9599-116">名為 `TestPhoto.jpg` 且位在 **c:\\** 的影像檔。</span><span class="sxs-lookup"><span data-stu-id="b9599-116">An image file that is named `TestPhoto.jpg` and located at **c:\\**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9599-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9599-117">See also</span></span>

- [<span data-ttu-id="b9599-118">如何：判斷編碼器所支援的參數</span><span class="sxs-lookup"><span data-stu-id="b9599-118">How to: Determine the Parameters Supported by an Encoder</span></span>](how-to-determine-the-parameters-supported-by-an-encoder.md)
- [<span data-ttu-id="b9599-119">點陣圖類型</span><span class="sxs-lookup"><span data-stu-id="b9599-119">Types of Bitmaps</span></span>](types-of-bitmaps.md)
- [<span data-ttu-id="b9599-120">使用 Managed GDI+ 中的影像編碼器和解碼器</span><span class="sxs-lookup"><span data-stu-id="b9599-120">Using Image Encoders and Decoders in Managed GDI+</span></span>](using-image-encoders-and-decoders-in-managed-gdi.md)
