---
title: OLE DB 結構描述集合
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 1ab6426875b73b400a59b7e4cf155615d7472d05
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514485"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="e0dce-102">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="e0dce-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="e0dce-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 OLE DB 提供者的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="e0dce-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="e0dce-104">Microsoft SQL Server OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="e0dce-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="e0dce-105">Microsoft SQL Server OLE DB 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="e0dce-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="e0dce-106">資料表</span><span class="sxs-lookup"><span data-stu-id="e0dce-106">Tables</span></span>  
  
-   <span data-ttu-id="e0dce-107">資料行</span><span class="sxs-lookup"><span data-stu-id="e0dce-107">Columns</span></span>  
  
-   <span data-ttu-id="e0dce-108">程序</span><span class="sxs-lookup"><span data-stu-id="e0dce-108">Procedures</span></span>  
  
-   <span data-ttu-id="e0dce-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e0dce-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="e0dce-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="e0dce-110">Catalog</span></span>  
  
-   <span data-ttu-id="e0dce-111">Indexes</span><span class="sxs-lookup"><span data-stu-id="e0dce-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="e0dce-112">資料表</span><span class="sxs-lookup"><span data-stu-id="e0dce-112">Tables</span></span>  
  
|<span data-ttu-id="e0dce-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-113">ColumnName</span></span>|<span data-ttu-id="e0dce-114">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-115">TABLE_CATALOG</span></span>|<span data-ttu-id="e0dce-116">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-116">String</span></span>|  
|<span data-ttu-id="e0dce-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="e0dce-118">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-118">String</span></span>|  
|<span data-ttu-id="e0dce-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-119">TABLE_NAME</span></span>|<span data-ttu-id="e0dce-120">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-120">String</span></span>|  
|<span data-ttu-id="e0dce-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-121">TABLE_TYPE</span></span>|<span data-ttu-id="e0dce-122">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-122">String</span></span>|  
|<span data-ttu-id="e0dce-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="e0dce-123">TABLE_GUID</span></span>|<span data-ttu-id="e0dce-124">Guid</span><span class="sxs-lookup"><span data-stu-id="e0dce-124">Guid</span></span>|  
|<span data-ttu-id="e0dce-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-125">DESCRIPTION</span></span>|<span data-ttu-id="e0dce-126">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-126">String</span></span>|  
|<span data-ttu-id="e0dce-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="e0dce-127">TABLE_PROPID</span></span>|<span data-ttu-id="e0dce-128">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-128">Int64</span></span>|  
|<span data-ttu-id="e0dce-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e0dce-129">DATE_CREATED</span></span>|<span data-ttu-id="e0dce-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-130">DateTime</span></span>|  
|<span data-ttu-id="e0dce-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e0dce-131">DATE_MODIFIED</span></span>|<span data-ttu-id="e0dce-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e0dce-133">資料行</span><span class="sxs-lookup"><span data-stu-id="e0dce-133">Columns</span></span>  
  
|<span data-ttu-id="e0dce-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-134">ColumnName</span></span>|<span data-ttu-id="e0dce-135">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-136">TABLE_CATALOG</span></span>|<span data-ttu-id="e0dce-137">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-137">String</span></span>|  
|<span data-ttu-id="e0dce-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="e0dce-139">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-139">String</span></span>|  
|<span data-ttu-id="e0dce-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-140">TABLE_NAME</span></span>|<span data-ttu-id="e0dce-141">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-141">String</span></span>|  
|<span data-ttu-id="e0dce-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-142">COLUMN_NAME</span></span>|<span data-ttu-id="e0dce-143">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-143">String</span></span>|  
|<span data-ttu-id="e0dce-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="e0dce-144">COLUMN_GUID</span></span>|<span data-ttu-id="e0dce-145">Guid</span><span class="sxs-lookup"><span data-stu-id="e0dce-145">Guid</span></span>|  
|<span data-ttu-id="e0dce-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="e0dce-146">COLUMN_PROPID</span></span>|<span data-ttu-id="e0dce-147">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-147">Int64</span></span>|  
|<span data-ttu-id="e0dce-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="e0dce-149">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-149">Int64</span></span>|  
|<span data-ttu-id="e0dce-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="e0dce-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="e0dce-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-151">Boolean</span></span>|  
|<span data-ttu-id="e0dce-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e0dce-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="e0dce-153">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-153">String</span></span>|  
|<span data-ttu-id="e0dce-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="e0dce-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="e0dce-155">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-155">Int64</span></span>|  
|<span data-ttu-id="e0dce-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e0dce-156">IS_NULLABLE</span></span>|<span data-ttu-id="e0dce-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-157">Boolean</span></span>|  
|<span data-ttu-id="e0dce-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-158">DATA_TYPE</span></span>|<span data-ttu-id="e0dce-159">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-159">Int32</span></span>|  
|<span data-ttu-id="e0dce-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="e0dce-160">TYPE_GUID</span></span>|<span data-ttu-id="e0dce-161">Guid</span><span class="sxs-lookup"><span data-stu-id="e0dce-161">Guid</span></span>|  
|<span data-ttu-id="e0dce-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e0dce-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="e0dce-163">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-163">Int64</span></span>|  
|<span data-ttu-id="e0dce-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e0dce-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="e0dce-165">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-165">Int64</span></span>|  
|<span data-ttu-id="e0dce-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e0dce-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="e0dce-167">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-167">Int32</span></span>|  
|<span data-ttu-id="e0dce-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="e0dce-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="e0dce-169">Int16</span><span class="sxs-lookup"><span data-stu-id="e0dce-169">Int16</span></span>|  
|<span data-ttu-id="e0dce-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e0dce-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="e0dce-171">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-171">Int64</span></span>|  
|<span data-ttu-id="e0dce-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="e0dce-173">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-173">String</span></span>|  
|<span data-ttu-id="e0dce-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="e0dce-175">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-175">String</span></span>|  
|<span data-ttu-id="e0dce-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="e0dce-177">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-177">String</span></span>|  
|<span data-ttu-id="e0dce-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="e0dce-179">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-179">String</span></span>|  
|<span data-ttu-id="e0dce-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="e0dce-181">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-181">String</span></span>|  
|<span data-ttu-id="e0dce-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-182">COLLATION_NAME</span></span>|<span data-ttu-id="e0dce-183">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-183">String</span></span>|  
|<span data-ttu-id="e0dce-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="e0dce-185">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-185">String</span></span>|  
|<span data-ttu-id="e0dce-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="e0dce-187">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-187">String</span></span>|  
|<span data-ttu-id="e0dce-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-188">DOMAIN_NAME</span></span>|<span data-ttu-id="e0dce-189">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-189">String</span></span>|  
|<span data-ttu-id="e0dce-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-190">DESCRIPTION</span></span>|<span data-ttu-id="e0dce-191">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-191">String</span></span>|  
|<span data-ttu-id="e0dce-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="e0dce-192">COLUMN_LCID</span></span>|<span data-ttu-id="e0dce-193">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-193">Int32</span></span>|  
|<span data-ttu-id="e0dce-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="e0dce-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="e0dce-195">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-195">Int32</span></span>|  
|<span data-ttu-id="e0dce-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="e0dce-196">COLUMN_SORTID</span></span>|<span data-ttu-id="e0dce-197">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-197">Int32</span></span>|  
|<span data-ttu-id="e0dce-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="e0dce-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="e0dce-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="e0dce-199">Byte[]</span></span>|  
|<span data-ttu-id="e0dce-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="e0dce-200">IS_COMPUTED</span></span>|<span data-ttu-id="e0dce-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e0dce-202">程序</span><span class="sxs-lookup"><span data-stu-id="e0dce-202">Procedures</span></span>  
  
|<span data-ttu-id="e0dce-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-203">ColumnName</span></span>|<span data-ttu-id="e0dce-204">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="e0dce-206">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-206">String</span></span>|  
|<span data-ttu-id="e0dce-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="e0dce-208">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-208">String</span></span>|  
|<span data-ttu-id="e0dce-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="e0dce-210">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-210">String</span></span>|  
|<span data-ttu-id="e0dce-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e0dce-212">Int16</span><span class="sxs-lookup"><span data-stu-id="e0dce-212">Int16</span></span>|  
|<span data-ttu-id="e0dce-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="e0dce-214">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-214">String</span></span>|  
|<span data-ttu-id="e0dce-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-215">DESCRIPTION</span></span>|<span data-ttu-id="e0dce-216">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-216">String</span></span>|  
|<span data-ttu-id="e0dce-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e0dce-217">DATE_CREATED</span></span>|<span data-ttu-id="e0dce-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-218">DateTime</span></span>|  
|<span data-ttu-id="e0dce-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e0dce-219">DATE_MODIFIED</span></span>|<span data-ttu-id="e0dce-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="e0dce-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e0dce-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="e0dce-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-222">ColumnName</span></span>|<span data-ttu-id="e0dce-223">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="e0dce-225">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-225">String</span></span>|  
|<span data-ttu-id="e0dce-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="e0dce-227">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-227">String</span></span>|  
|<span data-ttu-id="e0dce-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="e0dce-229">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-229">String</span></span>|  
|<span data-ttu-id="e0dce-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-230">PARAMETER_NAME</span></span>|<span data-ttu-id="e0dce-231">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-231">String</span></span>|  
|<span data-ttu-id="e0dce-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="e0dce-233">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-233">Int32</span></span>|  
|<span data-ttu-id="e0dce-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="e0dce-235">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-235">Int32</span></span>|  
|<span data-ttu-id="e0dce-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="e0dce-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="e0dce-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-237">Boolean</span></span>|  
|<span data-ttu-id="e0dce-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e0dce-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="e0dce-239">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-239">String</span></span>|  
|<span data-ttu-id="e0dce-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e0dce-240">IS_NULLABLE</span></span>|<span data-ttu-id="e0dce-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-241">Boolean</span></span>|  
|<span data-ttu-id="e0dce-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-242">DATA_TYPE</span></span>|<span data-ttu-id="e0dce-243">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-243">Int32</span></span>|  
|<span data-ttu-id="e0dce-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e0dce-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="e0dce-245">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-245">Int64</span></span>|  
|<span data-ttu-id="e0dce-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e0dce-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="e0dce-247">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-247">Int64</span></span>|  
|<span data-ttu-id="e0dce-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e0dce-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="e0dce-249">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-249">Int32</span></span>|  
|<span data-ttu-id="e0dce-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="e0dce-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="e0dce-251">Int16</span><span class="sxs-lookup"><span data-stu-id="e0dce-251">Int16</span></span>|  
|<span data-ttu-id="e0dce-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-252">DESCRIPTION</span></span>|<span data-ttu-id="e0dce-253">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-253">String</span></span>|  
|<span data-ttu-id="e0dce-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-254">TYPE_NAME</span></span>|<span data-ttu-id="e0dce-255">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-255">String</span></span>|  
|<span data-ttu-id="e0dce-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="e0dce-257">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="e0dce-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="e0dce-258">Catalog</span></span>  
  
|<span data-ttu-id="e0dce-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-259">ColumnName</span></span>|<span data-ttu-id="e0dce-260">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-261">CATALOG_NAME</span></span>|<span data-ttu-id="e0dce-262">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-262">String</span></span>|  
|<span data-ttu-id="e0dce-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-263">DESCRIPTION</span></span>|<span data-ttu-id="e0dce-264">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="e0dce-265">Indexes</span><span class="sxs-lookup"><span data-stu-id="e0dce-265">Indexes</span></span>  
  
|<span data-ttu-id="e0dce-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-266">ColumnName</span></span>|<span data-ttu-id="e0dce-267">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-268">TABLE_CATALOG</span></span>|<span data-ttu-id="e0dce-269">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-269">String</span></span>|  
|<span data-ttu-id="e0dce-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="e0dce-271">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-271">String</span></span>|  
|<span data-ttu-id="e0dce-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-272">TABLE_NAME</span></span>|<span data-ttu-id="e0dce-273">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-273">String</span></span>|  
|<span data-ttu-id="e0dce-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-274">INDEX_CATALOG</span></span>|<span data-ttu-id="e0dce-275">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-275">String</span></span>|  
|<span data-ttu-id="e0dce-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="e0dce-277">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-277">String</span></span>|  
|<span data-ttu-id="e0dce-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-278">INDEX_NAME</span></span>|<span data-ttu-id="e0dce-279">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-279">String</span></span>|  
|<span data-ttu-id="e0dce-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="e0dce-280">PRIMARY_KEY</span></span>|<span data-ttu-id="e0dce-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-281">Boolean</span></span>|  
|<span data-ttu-id="e0dce-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="e0dce-282">UNIQUE</span></span>|<span data-ttu-id="e0dce-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-283">Boolean</span></span>|  
|<span data-ttu-id="e0dce-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="e0dce-284">CLUSTERED</span></span>|<span data-ttu-id="e0dce-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-285">Boolean</span></span>|  
|<span data-ttu-id="e0dce-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-286">TYPE</span></span>|<span data-ttu-id="e0dce-287">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-287">Int32</span></span>|  
|<span data-ttu-id="e0dce-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="e0dce-288">FILL_FACTOR</span></span>|<span data-ttu-id="e0dce-289">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-289">Int32</span></span>|  
|<span data-ttu-id="e0dce-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="e0dce-290">INITIAL_SIZE</span></span>|<span data-ttu-id="e0dce-291">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-291">Int32</span></span>|  
|<span data-ttu-id="e0dce-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="e0dce-292">NULLS</span></span>|<span data-ttu-id="e0dce-293">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-293">Int32</span></span>|  
|<span data-ttu-id="e0dce-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="e0dce-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="e0dce-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-295">Boolean</span></span>|  
|<span data-ttu-id="e0dce-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="e0dce-296">AUTO_UPDATE</span></span>|<span data-ttu-id="e0dce-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-297">Boolean</span></span>|  
|<span data-ttu-id="e0dce-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="e0dce-298">NULL_COLLATION</span></span>|<span data-ttu-id="e0dce-299">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-299">Int32</span></span>|  
|<span data-ttu-id="e0dce-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="e0dce-301">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-301">Int64</span></span>|  
|<span data-ttu-id="e0dce-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-302">COLUMN_NAME</span></span>|<span data-ttu-id="e0dce-303">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-303">String</span></span>|  
|<span data-ttu-id="e0dce-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="e0dce-304">COLUMN_GUID</span></span>|<span data-ttu-id="e0dce-305">Guid</span><span class="sxs-lookup"><span data-stu-id="e0dce-305">Guid</span></span>|  
|<span data-ttu-id="e0dce-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="e0dce-306">COLUMN_PROPID</span></span>|<span data-ttu-id="e0dce-307">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-307">Int64</span></span>|  
|<span data-ttu-id="e0dce-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="e0dce-308">COLLATION</span></span>|<span data-ttu-id="e0dce-309">Int16</span><span class="sxs-lookup"><span data-stu-id="e0dce-309">Int16</span></span>|  
|<span data-ttu-id="e0dce-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="e0dce-310">CARDINALITY</span></span>|<span data-ttu-id="e0dce-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="e0dce-311">Decimal</span></span>|  
|<span data-ttu-id="e0dce-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="e0dce-312">PAGES</span></span>|<span data-ttu-id="e0dce-313">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-313">Int32</span></span>|  
|<span data-ttu-id="e0dce-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-314">FILTER_CONDITION</span></span>|<span data-ttu-id="e0dce-315">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-315">String</span></span>|  
|<span data-ttu-id="e0dce-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="e0dce-316">INTEGRATED</span></span>|<span data-ttu-id="e0dce-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="e0dce-318">Microsoft Oracle OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="e0dce-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="e0dce-319">除了通用結構描述集合之外，Microsoft Oracle OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="e0dce-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="e0dce-320">資料表</span><span class="sxs-lookup"><span data-stu-id="e0dce-320">Tables</span></span>  
  
-   <span data-ttu-id="e0dce-321">資料行</span><span class="sxs-lookup"><span data-stu-id="e0dce-321">Columns</span></span>  
  
-   <span data-ttu-id="e0dce-322">程序</span><span class="sxs-lookup"><span data-stu-id="e0dce-322">Procedures</span></span>  
  
-   <span data-ttu-id="e0dce-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e0dce-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="e0dce-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="e0dce-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="e0dce-325">檢視</span><span class="sxs-lookup"><span data-stu-id="e0dce-325">Views</span></span>  
  
-   <span data-ttu-id="e0dce-326">Indexes</span><span class="sxs-lookup"><span data-stu-id="e0dce-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="e0dce-327">資料表</span><span class="sxs-lookup"><span data-stu-id="e0dce-327">Tables</span></span>  
  
|<span data-ttu-id="e0dce-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-328">ColumnName</span></span>|<span data-ttu-id="e0dce-329">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-330">TABLE_CATALOG</span></span>|<span data-ttu-id="e0dce-331">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-331">String</span></span>|  
|<span data-ttu-id="e0dce-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="e0dce-333">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-333">String</span></span>|  
|<span data-ttu-id="e0dce-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-334">TABLE_NAME</span></span>|<span data-ttu-id="e0dce-335">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-335">String</span></span>|  
|<span data-ttu-id="e0dce-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-336">TABLE_TYPE</span></span>|<span data-ttu-id="e0dce-337">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-337">String</span></span>|  
|<span data-ttu-id="e0dce-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="e0dce-338">TABLE_GUID</span></span>|<span data-ttu-id="e0dce-339">Guid</span><span class="sxs-lookup"><span data-stu-id="e0dce-339">Guid</span></span>|  
|<span data-ttu-id="e0dce-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-340">DESCRIPTION</span></span>|<span data-ttu-id="e0dce-341">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-341">String</span></span>|  
|<span data-ttu-id="e0dce-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="e0dce-342">TABLE_PROPID</span></span>|<span data-ttu-id="e0dce-343">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-343">Int64</span></span>|  
|<span data-ttu-id="e0dce-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e0dce-344">DATE_CREATED</span></span>|<span data-ttu-id="e0dce-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-345">DateTime</span></span>|  
|<span data-ttu-id="e0dce-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e0dce-346">DATE_MODIFIED</span></span>|<span data-ttu-id="e0dce-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e0dce-348">資料行</span><span class="sxs-lookup"><span data-stu-id="e0dce-348">Columns</span></span>  
  
|<span data-ttu-id="e0dce-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-349">ColumnName</span></span>|<span data-ttu-id="e0dce-350">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-351">TABLE_CATALOG</span></span>|<span data-ttu-id="e0dce-352">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-352">String</span></span>|  
|<span data-ttu-id="e0dce-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="e0dce-354">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-354">String</span></span>|  
|<span data-ttu-id="e0dce-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-355">TABLE_NAME</span></span>|<span data-ttu-id="e0dce-356">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-356">String</span></span>|  
|<span data-ttu-id="e0dce-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-357">COLUMN_NAME</span></span>|<span data-ttu-id="e0dce-358">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-358">String</span></span>|  
|<span data-ttu-id="e0dce-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="e0dce-359">COLUMN_GUID</span></span>|<span data-ttu-id="e0dce-360">Guid</span><span class="sxs-lookup"><span data-stu-id="e0dce-360">Guid</span></span>|  
|<span data-ttu-id="e0dce-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="e0dce-361">COLUMN_PROPID</span></span>|<span data-ttu-id="e0dce-362">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-362">Int64</span></span>|  
|<span data-ttu-id="e0dce-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="e0dce-364">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-364">Int64</span></span>|  
|<span data-ttu-id="e0dce-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="e0dce-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="e0dce-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-366">Boolean</span></span>|  
|<span data-ttu-id="e0dce-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e0dce-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="e0dce-368">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-368">String</span></span>|  
|<span data-ttu-id="e0dce-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="e0dce-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="e0dce-370">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-370">Int64</span></span>|  
|<span data-ttu-id="e0dce-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e0dce-371">IS_NULLABLE</span></span>|<span data-ttu-id="e0dce-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-372">Boolean</span></span>|  
|<span data-ttu-id="e0dce-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-373">DATA_TYPE</span></span>|<span data-ttu-id="e0dce-374">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-374">Int32</span></span>|  
|<span data-ttu-id="e0dce-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="e0dce-375">TYPE_GUID</span></span>|<span data-ttu-id="e0dce-376">Guid</span><span class="sxs-lookup"><span data-stu-id="e0dce-376">Guid</span></span>|  
|<span data-ttu-id="e0dce-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e0dce-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="e0dce-378">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-378">Int64</span></span>|  
|<span data-ttu-id="e0dce-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e0dce-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="e0dce-380">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-380">Int64</span></span>|  
|<span data-ttu-id="e0dce-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e0dce-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="e0dce-382">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-382">Int32</span></span>|  
|<span data-ttu-id="e0dce-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="e0dce-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="e0dce-384">Int16</span><span class="sxs-lookup"><span data-stu-id="e0dce-384">Int16</span></span>|  
|<span data-ttu-id="e0dce-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e0dce-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="e0dce-386">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-386">Int64</span></span>|  
|<span data-ttu-id="e0dce-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="e0dce-388">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-388">String</span></span>|  
|<span data-ttu-id="e0dce-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="e0dce-390">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-390">String</span></span>|  
|<span data-ttu-id="e0dce-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="e0dce-392">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-392">String</span></span>|  
|<span data-ttu-id="e0dce-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="e0dce-394">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-394">String</span></span>|  
|<span data-ttu-id="e0dce-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="e0dce-396">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-396">String</span></span>|  
|<span data-ttu-id="e0dce-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-397">COLLATION_NAME</span></span>|<span data-ttu-id="e0dce-398">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-398">String</span></span>|  
|<span data-ttu-id="e0dce-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="e0dce-400">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-400">String</span></span>|  
|<span data-ttu-id="e0dce-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="e0dce-402">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-402">String</span></span>|  
|<span data-ttu-id="e0dce-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-403">DOMAIN_NAME</span></span>|<span data-ttu-id="e0dce-404">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-404">String</span></span>|  
|<span data-ttu-id="e0dce-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-405">DESCRIPTION</span></span>|<span data-ttu-id="e0dce-406">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e0dce-407">程序</span><span class="sxs-lookup"><span data-stu-id="e0dce-407">Procedures</span></span>  
  
|<span data-ttu-id="e0dce-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-408">ColumnName</span></span>|<span data-ttu-id="e0dce-409">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="e0dce-411">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-411">String</span></span>|  
|<span data-ttu-id="e0dce-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="e0dce-413">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-413">String</span></span>|  
|<span data-ttu-id="e0dce-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="e0dce-415">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-415">String</span></span>|  
|<span data-ttu-id="e0dce-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e0dce-417">Int16</span><span class="sxs-lookup"><span data-stu-id="e0dce-417">Int16</span></span>|  
|<span data-ttu-id="e0dce-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="e0dce-419">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-419">String</span></span>|  
|<span data-ttu-id="e0dce-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-420">DESCRIPTION</span></span>|<span data-ttu-id="e0dce-421">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-421">String</span></span>|  
|<span data-ttu-id="e0dce-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e0dce-422">DATE_CREATED</span></span>|<span data-ttu-id="e0dce-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-423">DateTime</span></span>|  
|<span data-ttu-id="e0dce-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e0dce-424">DATE_MODIFIED</span></span>|<span data-ttu-id="e0dce-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="e0dce-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="e0dce-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="e0dce-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-427">ColumnName</span></span>|<span data-ttu-id="e0dce-428">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="e0dce-430">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-430">String</span></span>|  
|<span data-ttu-id="e0dce-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="e0dce-432">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-432">String</span></span>|  
|<span data-ttu-id="e0dce-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="e0dce-434">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-434">String</span></span>|  
|<span data-ttu-id="e0dce-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-435">COLUMN_NAME</span></span>|<span data-ttu-id="e0dce-436">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-436">String</span></span>|  
|<span data-ttu-id="e0dce-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="e0dce-437">COLUMN_GUID</span></span>|<span data-ttu-id="e0dce-438">Guid</span><span class="sxs-lookup"><span data-stu-id="e0dce-438">Guid</span></span>|  
|<span data-ttu-id="e0dce-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="e0dce-439">COLUMN_PROPID</span></span>|<span data-ttu-id="e0dce-440">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-440">Int64</span></span>|  
|<span data-ttu-id="e0dce-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="e0dce-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="e0dce-442">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-442">Int64</span></span>|  
|<span data-ttu-id="e0dce-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="e0dce-444">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-444">Int64</span></span>|  
|<span data-ttu-id="e0dce-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e0dce-445">IS_NULLABLE</span></span>|<span data-ttu-id="e0dce-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-446">Boolean</span></span>|  
|<span data-ttu-id="e0dce-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-447">DATA_TYPE</span></span>|<span data-ttu-id="e0dce-448">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-448">Int32</span></span>|  
|<span data-ttu-id="e0dce-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="e0dce-449">TYPE_GUID</span></span>|<span data-ttu-id="e0dce-450">Guid</span><span class="sxs-lookup"><span data-stu-id="e0dce-450">Guid</span></span>|  
|<span data-ttu-id="e0dce-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e0dce-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="e0dce-452">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-452">Int64</span></span>|  
|<span data-ttu-id="e0dce-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e0dce-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="e0dce-454">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-454">Int64</span></span>|  
|<span data-ttu-id="e0dce-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e0dce-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="e0dce-456">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-456">Int32</span></span>|  
|<span data-ttu-id="e0dce-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="e0dce-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="e0dce-458">Int16</span><span class="sxs-lookup"><span data-stu-id="e0dce-458">Int16</span></span>|  
|<span data-ttu-id="e0dce-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-459">DESCRIPTION</span></span>|<span data-ttu-id="e0dce-460">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-460">String</span></span>|  
|<span data-ttu-id="e0dce-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="e0dce-461">OVERLOAD</span></span>|<span data-ttu-id="e0dce-462">Int16</span><span class="sxs-lookup"><span data-stu-id="e0dce-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="e0dce-463">檢視</span><span class="sxs-lookup"><span data-stu-id="e0dce-463">Views</span></span>  
  
|<span data-ttu-id="e0dce-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-464">ColumnName</span></span>|<span data-ttu-id="e0dce-465">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-466">TABLE_CATALOG</span></span>|<span data-ttu-id="e0dce-467">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-467">String</span></span>|  
|<span data-ttu-id="e0dce-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="e0dce-469">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-469">String</span></span>|  
|<span data-ttu-id="e0dce-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-470">TABLE_NAME</span></span>|<span data-ttu-id="e0dce-471">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-471">String</span></span>|  
|<span data-ttu-id="e0dce-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="e0dce-473">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-473">String</span></span>|  
|<span data-ttu-id="e0dce-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-474">CHECK_OPTION</span></span>|<span data-ttu-id="e0dce-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-475">Boolean</span></span>|  
|<span data-ttu-id="e0dce-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="e0dce-476">IS_UPDATABLE</span></span>|<span data-ttu-id="e0dce-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-477">Boolean</span></span>|  
|<span data-ttu-id="e0dce-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-478">DESCRIPTION</span></span>|<span data-ttu-id="e0dce-479">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-479">String</span></span>|  
|<span data-ttu-id="e0dce-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e0dce-480">DATE_CREATED</span></span>|<span data-ttu-id="e0dce-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-481">DateTime</span></span>|  
|<span data-ttu-id="e0dce-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e0dce-482">DATE_MODIFIED</span></span>|<span data-ttu-id="e0dce-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="e0dce-484">Indexes</span><span class="sxs-lookup"><span data-stu-id="e0dce-484">Indexes</span></span>  
  
|<span data-ttu-id="e0dce-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-485">ColumnName</span></span>|<span data-ttu-id="e0dce-486">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-487">TABLE_CATALOG</span></span>|<span data-ttu-id="e0dce-488">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-488">String</span></span>|  
|<span data-ttu-id="e0dce-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="e0dce-490">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-490">String</span></span>|  
|<span data-ttu-id="e0dce-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-491">TABLE_NAME</span></span>|<span data-ttu-id="e0dce-492">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-492">String</span></span>|  
|<span data-ttu-id="e0dce-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-493">INDEX_CATALOG</span></span>|<span data-ttu-id="e0dce-494">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-494">String</span></span>|  
|<span data-ttu-id="e0dce-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="e0dce-496">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-496">String</span></span>|  
|<span data-ttu-id="e0dce-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-497">INDEX_NAME</span></span>|<span data-ttu-id="e0dce-498">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-498">String</span></span>|  
|<span data-ttu-id="e0dce-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="e0dce-499">PRIMARY_KEY</span></span>|<span data-ttu-id="e0dce-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-500">Boolean</span></span>|  
|<span data-ttu-id="e0dce-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="e0dce-501">UNIQUE</span></span>|<span data-ttu-id="e0dce-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-502">Boolean</span></span>|  
|<span data-ttu-id="e0dce-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="e0dce-503">CLUSTERED</span></span>|<span data-ttu-id="e0dce-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-504">Boolean</span></span>|  
|<span data-ttu-id="e0dce-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-505">TYPE</span></span>|<span data-ttu-id="e0dce-506">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-506">Int32</span></span>|  
|<span data-ttu-id="e0dce-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="e0dce-507">FILL_FACTOR</span></span>|<span data-ttu-id="e0dce-508">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-508">Int32</span></span>|  
|<span data-ttu-id="e0dce-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="e0dce-509">INITIAL_SIZE</span></span>|<span data-ttu-id="e0dce-510">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-510">Int32</span></span>|  
|<span data-ttu-id="e0dce-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="e0dce-511">NULLS</span></span>|<span data-ttu-id="e0dce-512">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-512">Int32</span></span>|  
|<span data-ttu-id="e0dce-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="e0dce-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="e0dce-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-514">Boolean</span></span>|  
|<span data-ttu-id="e0dce-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="e0dce-515">AUTO_UPDATE</span></span>|<span data-ttu-id="e0dce-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-516">Boolean</span></span>|  
|<span data-ttu-id="e0dce-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="e0dce-517">NULL_COLLATION</span></span>|<span data-ttu-id="e0dce-518">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-518">Int32</span></span>|  
|<span data-ttu-id="e0dce-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="e0dce-520">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-520">Int64</span></span>|  
|<span data-ttu-id="e0dce-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-521">COLUMN_NAME</span></span>|<span data-ttu-id="e0dce-522">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-522">String</span></span>|  
|<span data-ttu-id="e0dce-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="e0dce-523">COLUMN_GUID</span></span>|<span data-ttu-id="e0dce-524">Guid</span><span class="sxs-lookup"><span data-stu-id="e0dce-524">Guid</span></span>|  
|<span data-ttu-id="e0dce-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="e0dce-525">COLUMN_PROPID</span></span>|<span data-ttu-id="e0dce-526">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-526">Int64</span></span>|  
|<span data-ttu-id="e0dce-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="e0dce-527">COLLATION</span></span>|<span data-ttu-id="e0dce-528">Int16</span><span class="sxs-lookup"><span data-stu-id="e0dce-528">Int16</span></span>|  
|<span data-ttu-id="e0dce-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="e0dce-529">CARDINALITY</span></span>|<span data-ttu-id="e0dce-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="e0dce-530">Decimal</span></span>|  
|<span data-ttu-id="e0dce-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="e0dce-531">PAGES</span></span>|<span data-ttu-id="e0dce-532">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-532">Int32</span></span>|  
|<span data-ttu-id="e0dce-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-533">FILTER_CONDITION</span></span>|<span data-ttu-id="e0dce-534">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-534">String</span></span>|  
|<span data-ttu-id="e0dce-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="e0dce-535">INTEGRATED</span></span>|<span data-ttu-id="e0dce-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="e0dce-537">Microsoft Jet OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="e0dce-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="e0dce-538">除了通用結構描述集合之外，Microsoft Jet OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="e0dce-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="e0dce-539">資料表</span><span class="sxs-lookup"><span data-stu-id="e0dce-539">Tables</span></span>  
  
-   <span data-ttu-id="e0dce-540">資料行</span><span class="sxs-lookup"><span data-stu-id="e0dce-540">Columns</span></span>  
  
-   <span data-ttu-id="e0dce-541">程序</span><span class="sxs-lookup"><span data-stu-id="e0dce-541">Procedures</span></span>  
  
-   <span data-ttu-id="e0dce-542">檢視</span><span class="sxs-lookup"><span data-stu-id="e0dce-542">Views</span></span>  
  
-   <span data-ttu-id="e0dce-543">Indexes</span><span class="sxs-lookup"><span data-stu-id="e0dce-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="e0dce-544">資料表</span><span class="sxs-lookup"><span data-stu-id="e0dce-544">Tables</span></span>  
  
|<span data-ttu-id="e0dce-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-545">ColumnName</span></span>|<span data-ttu-id="e0dce-546">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-547">TABLE_CATALOG</span></span>|<span data-ttu-id="e0dce-548">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-548">String</span></span>|  
|<span data-ttu-id="e0dce-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="e0dce-550">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-550">String</span></span>|  
|<span data-ttu-id="e0dce-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-551">TABLE_NAME</span></span>|<span data-ttu-id="e0dce-552">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-552">String</span></span>|  
|<span data-ttu-id="e0dce-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-553">TABLE_TYPE</span></span>|<span data-ttu-id="e0dce-554">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-554">String</span></span>|  
|<span data-ttu-id="e0dce-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="e0dce-555">TABLE_GUID</span></span>|<span data-ttu-id="e0dce-556">Guid</span><span class="sxs-lookup"><span data-stu-id="e0dce-556">Guid</span></span>|  
|<span data-ttu-id="e0dce-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-557">DESCRIPTION</span></span>|<span data-ttu-id="e0dce-558">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-558">String</span></span>|  
|<span data-ttu-id="e0dce-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="e0dce-559">TABLE_PROPID</span></span>|<span data-ttu-id="e0dce-560">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-560">Int64</span></span>|  
|<span data-ttu-id="e0dce-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e0dce-561">DATE_CREATED</span></span>|<span data-ttu-id="e0dce-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-562">DateTime</span></span>|  
|<span data-ttu-id="e0dce-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e0dce-563">DATE_MODIFIED</span></span>|<span data-ttu-id="e0dce-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="e0dce-565">資料行</span><span class="sxs-lookup"><span data-stu-id="e0dce-565">Columns</span></span>  
  
|<span data-ttu-id="e0dce-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-566">ColumnName</span></span>|<span data-ttu-id="e0dce-567">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-568">TABLE_CATALOG</span></span>|<span data-ttu-id="e0dce-569">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-569">String</span></span>|  
|<span data-ttu-id="e0dce-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="e0dce-571">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-571">String</span></span>|  
|<span data-ttu-id="e0dce-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-572">TABLE_NAME</span></span>|<span data-ttu-id="e0dce-573">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-573">String</span></span>|  
|<span data-ttu-id="e0dce-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-574">COLUMN_NAME</span></span>|<span data-ttu-id="e0dce-575">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-575">String</span></span>|  
|<span data-ttu-id="e0dce-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="e0dce-576">COLUMN_GUID</span></span>|<span data-ttu-id="e0dce-577">Guid</span><span class="sxs-lookup"><span data-stu-id="e0dce-577">Guid</span></span>|  
|<span data-ttu-id="e0dce-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="e0dce-578">COLUMN_PROPID</span></span>|<span data-ttu-id="e0dce-579">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-579">Int64</span></span>|  
|<span data-ttu-id="e0dce-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="e0dce-581">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-581">Int64</span></span>|  
|<span data-ttu-id="e0dce-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="e0dce-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="e0dce-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-583">Boolean</span></span>|  
|<span data-ttu-id="e0dce-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="e0dce-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="e0dce-585">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-585">String</span></span>|  
|<span data-ttu-id="e0dce-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="e0dce-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="e0dce-587">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-587">Int64</span></span>|  
|<span data-ttu-id="e0dce-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="e0dce-588">IS_NULLABLE</span></span>|<span data-ttu-id="e0dce-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-589">Boolean</span></span>|  
|<span data-ttu-id="e0dce-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-590">DATA_TYPE</span></span>|<span data-ttu-id="e0dce-591">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-591">Int32</span></span>|  
|<span data-ttu-id="e0dce-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="e0dce-592">TYPE_GUID</span></span>|<span data-ttu-id="e0dce-593">Guid</span><span class="sxs-lookup"><span data-stu-id="e0dce-593">Guid</span></span>|  
|<span data-ttu-id="e0dce-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e0dce-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="e0dce-595">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-595">Int64</span></span>|  
|<span data-ttu-id="e0dce-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="e0dce-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="e0dce-597">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-597">Int64</span></span>|  
|<span data-ttu-id="e0dce-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e0dce-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="e0dce-599">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-599">Int32</span></span>|  
|<span data-ttu-id="e0dce-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="e0dce-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="e0dce-601">Int16</span><span class="sxs-lookup"><span data-stu-id="e0dce-601">Int16</span></span>|  
|<span data-ttu-id="e0dce-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="e0dce-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="e0dce-603">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-603">Int64</span></span>|  
|<span data-ttu-id="e0dce-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="e0dce-605">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-605">String</span></span>|  
|<span data-ttu-id="e0dce-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="e0dce-607">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-607">String</span></span>|  
|<span data-ttu-id="e0dce-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="e0dce-609">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-609">String</span></span>|  
|<span data-ttu-id="e0dce-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="e0dce-611">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-611">String</span></span>|  
|<span data-ttu-id="e0dce-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="e0dce-613">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-613">String</span></span>|  
|<span data-ttu-id="e0dce-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-614">COLLATION_NAME</span></span>|<span data-ttu-id="e0dce-615">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-615">String</span></span>|  
|<span data-ttu-id="e0dce-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="e0dce-617">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-617">String</span></span>|  
|<span data-ttu-id="e0dce-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="e0dce-619">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-619">String</span></span>|  
|<span data-ttu-id="e0dce-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-620">DOMAIN_NAME</span></span>|<span data-ttu-id="e0dce-621">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-621">String</span></span>|  
|<span data-ttu-id="e0dce-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-622">DESCRIPTION</span></span>|<span data-ttu-id="e0dce-623">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="e0dce-624">程序</span><span class="sxs-lookup"><span data-stu-id="e0dce-624">Procedures</span></span>  
  
|<span data-ttu-id="e0dce-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-625">ColumnName</span></span>|<span data-ttu-id="e0dce-626">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="e0dce-628">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-628">String</span></span>|  
|<span data-ttu-id="e0dce-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="e0dce-630">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-630">String</span></span>|  
|<span data-ttu-id="e0dce-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="e0dce-632">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-632">String</span></span>|  
|<span data-ttu-id="e0dce-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="e0dce-634">Int16</span><span class="sxs-lookup"><span data-stu-id="e0dce-634">Int16</span></span>|  
|<span data-ttu-id="e0dce-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="e0dce-636">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-636">String</span></span>|  
|<span data-ttu-id="e0dce-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-637">DESCRIPTION</span></span>|<span data-ttu-id="e0dce-638">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-638">String</span></span>|  
|<span data-ttu-id="e0dce-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e0dce-639">DATE_CREATED</span></span>|<span data-ttu-id="e0dce-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-640">DateTime</span></span>|  
|<span data-ttu-id="e0dce-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e0dce-641">DATE_MODIFIED</span></span>|<span data-ttu-id="e0dce-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="e0dce-643">檢視</span><span class="sxs-lookup"><span data-stu-id="e0dce-643">Views</span></span>  
  
|<span data-ttu-id="e0dce-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-644">ColumnName</span></span>|<span data-ttu-id="e0dce-645">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-646">TABLE_CATALOG</span></span>|<span data-ttu-id="e0dce-647">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-647">String</span></span>|  
|<span data-ttu-id="e0dce-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="e0dce-649">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-649">String</span></span>|  
|<span data-ttu-id="e0dce-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-650">TABLE_NAME</span></span>|<span data-ttu-id="e0dce-651">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-651">String</span></span>|  
|<span data-ttu-id="e0dce-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="e0dce-653">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-653">String</span></span>|  
|<span data-ttu-id="e0dce-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-654">CHECK_OPTION</span></span>|<span data-ttu-id="e0dce-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-655">Boolean</span></span>|  
|<span data-ttu-id="e0dce-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="e0dce-656">IS_UPDATABLE</span></span>|<span data-ttu-id="e0dce-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-657">Boolean</span></span>|  
|<span data-ttu-id="e0dce-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="e0dce-658">DESCRIPTION</span></span>|<span data-ttu-id="e0dce-659">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-659">String</span></span>|  
|<span data-ttu-id="e0dce-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="e0dce-660">DATE_CREATED</span></span>|<span data-ttu-id="e0dce-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-661">DateTime</span></span>|  
|<span data-ttu-id="e0dce-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="e0dce-662">DATE_MODIFIED</span></span>|<span data-ttu-id="e0dce-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="e0dce-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="e0dce-664">Indexes</span><span class="sxs-lookup"><span data-stu-id="e0dce-664">Indexes</span></span>  
  
|<span data-ttu-id="e0dce-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="e0dce-665">ColumnName</span></span>|<span data-ttu-id="e0dce-666">DataType</span><span class="sxs-lookup"><span data-stu-id="e0dce-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="e0dce-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-667">TABLE_CATALOG</span></span>|<span data-ttu-id="e0dce-668">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-668">String</span></span>|  
|<span data-ttu-id="e0dce-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="e0dce-670">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-670">String</span></span>|  
|<span data-ttu-id="e0dce-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-671">TABLE_NAME</span></span>|<span data-ttu-id="e0dce-672">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-672">String</span></span>|  
|<span data-ttu-id="e0dce-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="e0dce-673">INDEX_CATALOG</span></span>|<span data-ttu-id="e0dce-674">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-674">String</span></span>|  
|<span data-ttu-id="e0dce-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="e0dce-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="e0dce-676">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-676">String</span></span>|  
|<span data-ttu-id="e0dce-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-677">INDEX_NAME</span></span>|<span data-ttu-id="e0dce-678">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-678">String</span></span>|  
|<span data-ttu-id="e0dce-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="e0dce-679">PRIMARY_KEY</span></span>|<span data-ttu-id="e0dce-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-680">Boolean</span></span>|  
|<span data-ttu-id="e0dce-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="e0dce-681">UNIQUE</span></span>|<span data-ttu-id="e0dce-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-682">Boolean</span></span>|  
|<span data-ttu-id="e0dce-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="e0dce-683">CLUSTERED</span></span>|<span data-ttu-id="e0dce-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-684">Boolean</span></span>|  
|<span data-ttu-id="e0dce-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="e0dce-685">TYPE</span></span>|<span data-ttu-id="e0dce-686">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-686">Int32</span></span>|  
|<span data-ttu-id="e0dce-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="e0dce-687">FILL_FACTOR</span></span>|<span data-ttu-id="e0dce-688">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-688">Int32</span></span>|  
|<span data-ttu-id="e0dce-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="e0dce-689">INITIAL_SIZE</span></span>|<span data-ttu-id="e0dce-690">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-690">Int32</span></span>|  
|<span data-ttu-id="e0dce-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="e0dce-691">NULLS</span></span>|<span data-ttu-id="e0dce-692">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-692">Int32</span></span>|  
|<span data-ttu-id="e0dce-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="e0dce-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="e0dce-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-694">Boolean</span></span>|  
|<span data-ttu-id="e0dce-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="e0dce-695">AUTO_UPDATE</span></span>|<span data-ttu-id="e0dce-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-696">Boolean</span></span>|  
|<span data-ttu-id="e0dce-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="e0dce-697">NULL_COLLATION</span></span>|<span data-ttu-id="e0dce-698">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-698">Int32</span></span>|  
|<span data-ttu-id="e0dce-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="e0dce-700">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-700">Int64</span></span>|  
|<span data-ttu-id="e0dce-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="e0dce-701">COLUMN_NAME</span></span>|<span data-ttu-id="e0dce-702">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-702">String</span></span>|  
|<span data-ttu-id="e0dce-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="e0dce-703">COLUMN_GUID</span></span>|<span data-ttu-id="e0dce-704">Guid</span><span class="sxs-lookup"><span data-stu-id="e0dce-704">Guid</span></span>|  
|<span data-ttu-id="e0dce-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="e0dce-705">COLUMN_PROPID</span></span>|<span data-ttu-id="e0dce-706">Int64</span><span class="sxs-lookup"><span data-stu-id="e0dce-706">Int64</span></span>|  
|<span data-ttu-id="e0dce-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="e0dce-707">COLLATION</span></span>|<span data-ttu-id="e0dce-708">Int16</span><span class="sxs-lookup"><span data-stu-id="e0dce-708">Int16</span></span>|  
|<span data-ttu-id="e0dce-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="e0dce-709">CARDINALITY</span></span>|<span data-ttu-id="e0dce-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="e0dce-710">Decimal</span></span>|  
|<span data-ttu-id="e0dce-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="e0dce-711">PAGES</span></span>|<span data-ttu-id="e0dce-712">Int32</span><span class="sxs-lookup"><span data-stu-id="e0dce-712">Int32</span></span>|  
|<span data-ttu-id="e0dce-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="e0dce-713">FILTER_CONDITION</span></span>|<span data-ttu-id="e0dce-714">String</span><span class="sxs-lookup"><span data-stu-id="e0dce-714">String</span></span>|  
|<span data-ttu-id="e0dce-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="e0dce-715">INTEGRATED</span></span>|<span data-ttu-id="e0dce-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="e0dce-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e0dce-717">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e0dce-717">See Also</span></span>  
 [<span data-ttu-id="e0dce-718">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="e0dce-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
