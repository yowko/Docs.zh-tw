---
title: OLE DB 結構描述集合
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: 6dc187b0a876d9e167a74f2381db156dde2764fe
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771991"
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="8f50f-102">OLE DB 結構描述集合</span><span class="sxs-lookup"><span data-stu-id="8f50f-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="8f50f-103">本節將討論 Microsoft SQL Server、Oracle 和 Microsoft Jet 之 OLE DB 提供者的結構描述集合支援。</span><span class="sxs-lookup"><span data-stu-id="8f50f-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="8f50f-104">Microsoft SQL Server OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="8f50f-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="8f50f-105">Microsoft SQL Server OLE DB 驅動程式支援下列特定結構描述集合除了通用結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="8f50f-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="8f50f-106">資料表</span><span class="sxs-lookup"><span data-stu-id="8f50f-106">Tables</span></span>  
  
- <span data-ttu-id="8f50f-107">資料行</span><span class="sxs-lookup"><span data-stu-id="8f50f-107">Columns</span></span>  
  
- <span data-ttu-id="8f50f-108">程序</span><span class="sxs-lookup"><span data-stu-id="8f50f-108">Procedures</span></span>  
  
- <span data-ttu-id="8f50f-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8f50f-109">ProcedureParameters</span></span>  
  
- <span data-ttu-id="8f50f-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="8f50f-110">Catalog</span></span>  
  
- <span data-ttu-id="8f50f-111">索引</span><span class="sxs-lookup"><span data-stu-id="8f50f-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="8f50f-112">資料表</span><span class="sxs-lookup"><span data-stu-id="8f50f-112">Tables</span></span>  
  
|<span data-ttu-id="8f50f-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-113">ColumnName</span></span>|<span data-ttu-id="8f50f-114">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-115">TABLE_CATALOG</span></span>|<span data-ttu-id="8f50f-116">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-116">String</span></span>|  
|<span data-ttu-id="8f50f-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="8f50f-118">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-118">String</span></span>|  
|<span data-ttu-id="8f50f-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-119">TABLE_NAME</span></span>|<span data-ttu-id="8f50f-120">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-120">String</span></span>|  
|<span data-ttu-id="8f50f-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-121">TABLE_TYPE</span></span>|<span data-ttu-id="8f50f-122">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-122">String</span></span>|  
|<span data-ttu-id="8f50f-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="8f50f-123">TABLE_GUID</span></span>|<span data-ttu-id="8f50f-124">Guid</span><span class="sxs-lookup"><span data-stu-id="8f50f-124">Guid</span></span>|  
|<span data-ttu-id="8f50f-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-125">DESCRIPTION</span></span>|<span data-ttu-id="8f50f-126">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-126">String</span></span>|  
|<span data-ttu-id="8f50f-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="8f50f-127">TABLE_PROPID</span></span>|<span data-ttu-id="8f50f-128">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-128">Int64</span></span>|  
|<span data-ttu-id="8f50f-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8f50f-129">DATE_CREATED</span></span>|<span data-ttu-id="8f50f-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-130">DateTime</span></span>|  
|<span data-ttu-id="8f50f-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8f50f-131">DATE_MODIFIED</span></span>|<span data-ttu-id="8f50f-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="8f50f-133">資料行</span><span class="sxs-lookup"><span data-stu-id="8f50f-133">Columns</span></span>  
  
|<span data-ttu-id="8f50f-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-134">ColumnName</span></span>|<span data-ttu-id="8f50f-135">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-136">TABLE_CATALOG</span></span>|<span data-ttu-id="8f50f-137">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-137">String</span></span>|  
|<span data-ttu-id="8f50f-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="8f50f-139">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-139">String</span></span>|  
|<span data-ttu-id="8f50f-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-140">TABLE_NAME</span></span>|<span data-ttu-id="8f50f-141">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-141">String</span></span>|  
|<span data-ttu-id="8f50f-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-142">COLUMN_NAME</span></span>|<span data-ttu-id="8f50f-143">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-143">String</span></span>|  
|<span data-ttu-id="8f50f-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8f50f-144">COLUMN_GUID</span></span>|<span data-ttu-id="8f50f-145">Guid</span><span class="sxs-lookup"><span data-stu-id="8f50f-145">Guid</span></span>|  
|<span data-ttu-id="8f50f-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8f50f-146">COLUMN_PROPID</span></span>|<span data-ttu-id="8f50f-147">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-147">Int64</span></span>|  
|<span data-ttu-id="8f50f-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="8f50f-149">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-149">Int64</span></span>|  
|<span data-ttu-id="8f50f-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="8f50f-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="8f50f-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-151">Boolean</span></span>|  
|<span data-ttu-id="8f50f-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="8f50f-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="8f50f-153">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-153">String</span></span>|  
|<span data-ttu-id="8f50f-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="8f50f-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="8f50f-155">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-155">Int64</span></span>|  
|<span data-ttu-id="8f50f-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8f50f-156">IS_NULLABLE</span></span>|<span data-ttu-id="8f50f-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-157">Boolean</span></span>|  
|<span data-ttu-id="8f50f-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-158">DATA_TYPE</span></span>|<span data-ttu-id="8f50f-159">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-159">Int32</span></span>|  
|<span data-ttu-id="8f50f-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="8f50f-160">TYPE_GUID</span></span>|<span data-ttu-id="8f50f-161">Guid</span><span class="sxs-lookup"><span data-stu-id="8f50f-161">Guid</span></span>|  
|<span data-ttu-id="8f50f-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8f50f-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8f50f-163">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-163">Int64</span></span>|  
|<span data-ttu-id="8f50f-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8f50f-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8f50f-165">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-165">Int64</span></span>|  
|<span data-ttu-id="8f50f-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8f50f-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8f50f-167">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-167">Int32</span></span>|  
|<span data-ttu-id="8f50f-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8f50f-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="8f50f-169">Int16</span><span class="sxs-lookup"><span data-stu-id="8f50f-169">Int16</span></span>|  
|<span data-ttu-id="8f50f-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8f50f-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="8f50f-171">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-171">Int64</span></span>|  
|<span data-ttu-id="8f50f-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="8f50f-173">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-173">String</span></span>|  
|<span data-ttu-id="8f50f-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="8f50f-175">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-175">String</span></span>|  
|<span data-ttu-id="8f50f-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="8f50f-177">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-177">String</span></span>|  
|<span data-ttu-id="8f50f-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="8f50f-179">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-179">String</span></span>|  
|<span data-ttu-id="8f50f-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="8f50f-181">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-181">String</span></span>|  
|<span data-ttu-id="8f50f-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-182">COLLATION_NAME</span></span>|<span data-ttu-id="8f50f-183">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-183">String</span></span>|  
|<span data-ttu-id="8f50f-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="8f50f-185">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-185">String</span></span>|  
|<span data-ttu-id="8f50f-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="8f50f-187">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-187">String</span></span>|  
|<span data-ttu-id="8f50f-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-188">DOMAIN_NAME</span></span>|<span data-ttu-id="8f50f-189">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-189">String</span></span>|  
|<span data-ttu-id="8f50f-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-190">DESCRIPTION</span></span>|<span data-ttu-id="8f50f-191">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-191">String</span></span>|  
|<span data-ttu-id="8f50f-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="8f50f-192">COLUMN_LCID</span></span>|<span data-ttu-id="8f50f-193">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-193">Int32</span></span>|  
|<span data-ttu-id="8f50f-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="8f50f-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="8f50f-195">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-195">Int32</span></span>|  
|<span data-ttu-id="8f50f-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="8f50f-196">COLUMN_SORTID</span></span>|<span data-ttu-id="8f50f-197">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-197">Int32</span></span>|  
|<span data-ttu-id="8f50f-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="8f50f-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="8f50f-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="8f50f-199">Byte[]</span></span>|  
|<span data-ttu-id="8f50f-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="8f50f-200">IS_COMPUTED</span></span>|<span data-ttu-id="8f50f-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="8f50f-202">程序</span><span class="sxs-lookup"><span data-stu-id="8f50f-202">Procedures</span></span>  
  
|<span data-ttu-id="8f50f-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-203">ColumnName</span></span>|<span data-ttu-id="8f50f-204">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8f50f-206">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-206">String</span></span>|  
|<span data-ttu-id="8f50f-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8f50f-208">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-208">String</span></span>|  
|<span data-ttu-id="8f50f-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="8f50f-210">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-210">String</span></span>|  
|<span data-ttu-id="8f50f-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="8f50f-212">Int16</span><span class="sxs-lookup"><span data-stu-id="8f50f-212">Int16</span></span>|  
|<span data-ttu-id="8f50f-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="8f50f-214">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-214">String</span></span>|  
|<span data-ttu-id="8f50f-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-215">DESCRIPTION</span></span>|<span data-ttu-id="8f50f-216">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-216">String</span></span>|  
|<span data-ttu-id="8f50f-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8f50f-217">DATE_CREATED</span></span>|<span data-ttu-id="8f50f-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-218">DateTime</span></span>|  
|<span data-ttu-id="8f50f-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8f50f-219">DATE_MODIFIED</span></span>|<span data-ttu-id="8f50f-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="8f50f-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8f50f-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="8f50f-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-222">ColumnName</span></span>|<span data-ttu-id="8f50f-223">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8f50f-225">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-225">String</span></span>|  
|<span data-ttu-id="8f50f-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8f50f-227">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-227">String</span></span>|  
|<span data-ttu-id="8f50f-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="8f50f-229">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-229">String</span></span>|  
|<span data-ttu-id="8f50f-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-230">PARAMETER_NAME</span></span>|<span data-ttu-id="8f50f-231">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-231">String</span></span>|  
|<span data-ttu-id="8f50f-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="8f50f-233">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-233">Int32</span></span>|  
|<span data-ttu-id="8f50f-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="8f50f-235">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-235">Int32</span></span>|  
|<span data-ttu-id="8f50f-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="8f50f-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="8f50f-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-237">Boolean</span></span>|  
|<span data-ttu-id="8f50f-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="8f50f-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="8f50f-239">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-239">String</span></span>|  
|<span data-ttu-id="8f50f-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8f50f-240">IS_NULLABLE</span></span>|<span data-ttu-id="8f50f-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-241">Boolean</span></span>|  
|<span data-ttu-id="8f50f-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-242">DATA_TYPE</span></span>|<span data-ttu-id="8f50f-243">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-243">Int32</span></span>|  
|<span data-ttu-id="8f50f-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8f50f-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8f50f-245">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-245">Int64</span></span>|  
|<span data-ttu-id="8f50f-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8f50f-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8f50f-247">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-247">Int64</span></span>|  
|<span data-ttu-id="8f50f-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8f50f-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8f50f-249">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-249">Int32</span></span>|  
|<span data-ttu-id="8f50f-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8f50f-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="8f50f-251">Int16</span><span class="sxs-lookup"><span data-stu-id="8f50f-251">Int16</span></span>|  
|<span data-ttu-id="8f50f-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-252">DESCRIPTION</span></span>|<span data-ttu-id="8f50f-253">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-253">String</span></span>|  
|<span data-ttu-id="8f50f-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-254">TYPE_NAME</span></span>|<span data-ttu-id="8f50f-255">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-255">String</span></span>|  
|<span data-ttu-id="8f50f-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="8f50f-257">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="8f50f-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="8f50f-258">Catalog</span></span>  
  
|<span data-ttu-id="8f50f-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-259">ColumnName</span></span>|<span data-ttu-id="8f50f-260">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-261">CATALOG_NAME</span></span>|<span data-ttu-id="8f50f-262">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-262">String</span></span>|  
|<span data-ttu-id="8f50f-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-263">DESCRIPTION</span></span>|<span data-ttu-id="8f50f-264">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="8f50f-265">索引</span><span class="sxs-lookup"><span data-stu-id="8f50f-265">Indexes</span></span>  
  
|<span data-ttu-id="8f50f-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-266">ColumnName</span></span>|<span data-ttu-id="8f50f-267">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-268">TABLE_CATALOG</span></span>|<span data-ttu-id="8f50f-269">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-269">String</span></span>|  
|<span data-ttu-id="8f50f-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="8f50f-271">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-271">String</span></span>|  
|<span data-ttu-id="8f50f-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-272">TABLE_NAME</span></span>|<span data-ttu-id="8f50f-273">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-273">String</span></span>|  
|<span data-ttu-id="8f50f-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-274">INDEX_CATALOG</span></span>|<span data-ttu-id="8f50f-275">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-275">String</span></span>|  
|<span data-ttu-id="8f50f-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="8f50f-277">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-277">String</span></span>|  
|<span data-ttu-id="8f50f-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-278">INDEX_NAME</span></span>|<span data-ttu-id="8f50f-279">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-279">String</span></span>|  
|<span data-ttu-id="8f50f-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="8f50f-280">PRIMARY_KEY</span></span>|<span data-ttu-id="8f50f-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-281">Boolean</span></span>|  
|<span data-ttu-id="8f50f-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="8f50f-282">UNIQUE</span></span>|<span data-ttu-id="8f50f-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-283">Boolean</span></span>|  
|<span data-ttu-id="8f50f-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="8f50f-284">CLUSTERED</span></span>|<span data-ttu-id="8f50f-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-285">Boolean</span></span>|  
|<span data-ttu-id="8f50f-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-286">TYPE</span></span>|<span data-ttu-id="8f50f-287">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-287">Int32</span></span>|  
|<span data-ttu-id="8f50f-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="8f50f-288">FILL_FACTOR</span></span>|<span data-ttu-id="8f50f-289">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-289">Int32</span></span>|  
|<span data-ttu-id="8f50f-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="8f50f-290">INITIAL_SIZE</span></span>|<span data-ttu-id="8f50f-291">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-291">Int32</span></span>|  
|<span data-ttu-id="8f50f-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="8f50f-292">NULLS</span></span>|<span data-ttu-id="8f50f-293">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-293">Int32</span></span>|  
|<span data-ttu-id="8f50f-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="8f50f-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="8f50f-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-295">Boolean</span></span>|  
|<span data-ttu-id="8f50f-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="8f50f-296">AUTO_UPDATE</span></span>|<span data-ttu-id="8f50f-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-297">Boolean</span></span>|  
|<span data-ttu-id="8f50f-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="8f50f-298">NULL_COLLATION</span></span>|<span data-ttu-id="8f50f-299">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-299">Int32</span></span>|  
|<span data-ttu-id="8f50f-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="8f50f-301">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-301">Int64</span></span>|  
|<span data-ttu-id="8f50f-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-302">COLUMN_NAME</span></span>|<span data-ttu-id="8f50f-303">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-303">String</span></span>|  
|<span data-ttu-id="8f50f-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8f50f-304">COLUMN_GUID</span></span>|<span data-ttu-id="8f50f-305">Guid</span><span class="sxs-lookup"><span data-stu-id="8f50f-305">Guid</span></span>|  
|<span data-ttu-id="8f50f-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8f50f-306">COLUMN_PROPID</span></span>|<span data-ttu-id="8f50f-307">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-307">Int64</span></span>|  
|<span data-ttu-id="8f50f-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="8f50f-308">COLLATION</span></span>|<span data-ttu-id="8f50f-309">Int16</span><span class="sxs-lookup"><span data-stu-id="8f50f-309">Int16</span></span>|  
|<span data-ttu-id="8f50f-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="8f50f-310">CARDINALITY</span></span>|<span data-ttu-id="8f50f-311">Decimal</span><span class="sxs-lookup"><span data-stu-id="8f50f-311">Decimal</span></span>|  
|<span data-ttu-id="8f50f-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="8f50f-312">PAGES</span></span>|<span data-ttu-id="8f50f-313">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-313">Int32</span></span>|  
|<span data-ttu-id="8f50f-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-314">FILTER_CONDITION</span></span>|<span data-ttu-id="8f50f-315">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-315">String</span></span>|  
|<span data-ttu-id="8f50f-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="8f50f-316">INTEGRATED</span></span>|<span data-ttu-id="8f50f-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="8f50f-318">Microsoft Oracle OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="8f50f-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="8f50f-319">除了通用結構描述集合之外，Microsoft Oracle OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="8f50f-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="8f50f-320">資料表</span><span class="sxs-lookup"><span data-stu-id="8f50f-320">Tables</span></span>  
  
- <span data-ttu-id="8f50f-321">資料行</span><span class="sxs-lookup"><span data-stu-id="8f50f-321">Columns</span></span>  
  
- <span data-ttu-id="8f50f-322">程序</span><span class="sxs-lookup"><span data-stu-id="8f50f-322">Procedures</span></span>  
  
- <span data-ttu-id="8f50f-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="8f50f-323">ProcedureColumns</span></span>  
  
- <span data-ttu-id="8f50f-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="8f50f-324">ProcedureParameters</span></span>  
  
- <span data-ttu-id="8f50f-325">檢視</span><span class="sxs-lookup"><span data-stu-id="8f50f-325">Views</span></span>  
  
- <span data-ttu-id="8f50f-326">索引</span><span class="sxs-lookup"><span data-stu-id="8f50f-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="8f50f-327">資料表</span><span class="sxs-lookup"><span data-stu-id="8f50f-327">Tables</span></span>  
  
|<span data-ttu-id="8f50f-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-328">ColumnName</span></span>|<span data-ttu-id="8f50f-329">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-330">TABLE_CATALOG</span></span>|<span data-ttu-id="8f50f-331">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-331">String</span></span>|  
|<span data-ttu-id="8f50f-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="8f50f-333">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-333">String</span></span>|  
|<span data-ttu-id="8f50f-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-334">TABLE_NAME</span></span>|<span data-ttu-id="8f50f-335">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-335">String</span></span>|  
|<span data-ttu-id="8f50f-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-336">TABLE_TYPE</span></span>|<span data-ttu-id="8f50f-337">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-337">String</span></span>|  
|<span data-ttu-id="8f50f-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="8f50f-338">TABLE_GUID</span></span>|<span data-ttu-id="8f50f-339">Guid</span><span class="sxs-lookup"><span data-stu-id="8f50f-339">Guid</span></span>|  
|<span data-ttu-id="8f50f-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-340">DESCRIPTION</span></span>|<span data-ttu-id="8f50f-341">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-341">String</span></span>|  
|<span data-ttu-id="8f50f-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="8f50f-342">TABLE_PROPID</span></span>|<span data-ttu-id="8f50f-343">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-343">Int64</span></span>|  
|<span data-ttu-id="8f50f-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8f50f-344">DATE_CREATED</span></span>|<span data-ttu-id="8f50f-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-345">DateTime</span></span>|  
|<span data-ttu-id="8f50f-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8f50f-346">DATE_MODIFIED</span></span>|<span data-ttu-id="8f50f-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="8f50f-348">資料行</span><span class="sxs-lookup"><span data-stu-id="8f50f-348">Columns</span></span>  
  
|<span data-ttu-id="8f50f-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-349">ColumnName</span></span>|<span data-ttu-id="8f50f-350">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-351">TABLE_CATALOG</span></span>|<span data-ttu-id="8f50f-352">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-352">String</span></span>|  
|<span data-ttu-id="8f50f-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="8f50f-354">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-354">String</span></span>|  
|<span data-ttu-id="8f50f-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-355">TABLE_NAME</span></span>|<span data-ttu-id="8f50f-356">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-356">String</span></span>|  
|<span data-ttu-id="8f50f-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-357">COLUMN_NAME</span></span>|<span data-ttu-id="8f50f-358">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-358">String</span></span>|  
|<span data-ttu-id="8f50f-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8f50f-359">COLUMN_GUID</span></span>|<span data-ttu-id="8f50f-360">Guid</span><span class="sxs-lookup"><span data-stu-id="8f50f-360">Guid</span></span>|  
|<span data-ttu-id="8f50f-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8f50f-361">COLUMN_PROPID</span></span>|<span data-ttu-id="8f50f-362">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-362">Int64</span></span>|  
|<span data-ttu-id="8f50f-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="8f50f-364">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-364">Int64</span></span>|  
|<span data-ttu-id="8f50f-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="8f50f-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="8f50f-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-366">Boolean</span></span>|  
|<span data-ttu-id="8f50f-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="8f50f-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="8f50f-368">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-368">String</span></span>|  
|<span data-ttu-id="8f50f-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="8f50f-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="8f50f-370">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-370">Int64</span></span>|  
|<span data-ttu-id="8f50f-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8f50f-371">IS_NULLABLE</span></span>|<span data-ttu-id="8f50f-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-372">Boolean</span></span>|  
|<span data-ttu-id="8f50f-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-373">DATA_TYPE</span></span>|<span data-ttu-id="8f50f-374">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-374">Int32</span></span>|  
|<span data-ttu-id="8f50f-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="8f50f-375">TYPE_GUID</span></span>|<span data-ttu-id="8f50f-376">Guid</span><span class="sxs-lookup"><span data-stu-id="8f50f-376">Guid</span></span>|  
|<span data-ttu-id="8f50f-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8f50f-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8f50f-378">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-378">Int64</span></span>|  
|<span data-ttu-id="8f50f-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8f50f-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8f50f-380">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-380">Int64</span></span>|  
|<span data-ttu-id="8f50f-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8f50f-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8f50f-382">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-382">Int32</span></span>|  
|<span data-ttu-id="8f50f-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8f50f-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="8f50f-384">Int16</span><span class="sxs-lookup"><span data-stu-id="8f50f-384">Int16</span></span>|  
|<span data-ttu-id="8f50f-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8f50f-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="8f50f-386">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-386">Int64</span></span>|  
|<span data-ttu-id="8f50f-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="8f50f-388">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-388">String</span></span>|  
|<span data-ttu-id="8f50f-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="8f50f-390">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-390">String</span></span>|  
|<span data-ttu-id="8f50f-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="8f50f-392">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-392">String</span></span>|  
|<span data-ttu-id="8f50f-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="8f50f-394">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-394">String</span></span>|  
|<span data-ttu-id="8f50f-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="8f50f-396">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-396">String</span></span>|  
|<span data-ttu-id="8f50f-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-397">COLLATION_NAME</span></span>|<span data-ttu-id="8f50f-398">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-398">String</span></span>|  
|<span data-ttu-id="8f50f-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="8f50f-400">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-400">String</span></span>|  
|<span data-ttu-id="8f50f-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="8f50f-402">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-402">String</span></span>|  
|<span data-ttu-id="8f50f-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-403">DOMAIN_NAME</span></span>|<span data-ttu-id="8f50f-404">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-404">String</span></span>|  
|<span data-ttu-id="8f50f-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-405">DESCRIPTION</span></span>|<span data-ttu-id="8f50f-406">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="8f50f-407">程序</span><span class="sxs-lookup"><span data-stu-id="8f50f-407">Procedures</span></span>  
  
|<span data-ttu-id="8f50f-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-408">ColumnName</span></span>|<span data-ttu-id="8f50f-409">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8f50f-411">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-411">String</span></span>|  
|<span data-ttu-id="8f50f-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8f50f-413">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-413">String</span></span>|  
|<span data-ttu-id="8f50f-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="8f50f-415">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-415">String</span></span>|  
|<span data-ttu-id="8f50f-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="8f50f-417">Int16</span><span class="sxs-lookup"><span data-stu-id="8f50f-417">Int16</span></span>|  
|<span data-ttu-id="8f50f-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="8f50f-419">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-419">String</span></span>|  
|<span data-ttu-id="8f50f-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-420">DESCRIPTION</span></span>|<span data-ttu-id="8f50f-421">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-421">String</span></span>|  
|<span data-ttu-id="8f50f-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8f50f-422">DATE_CREATED</span></span>|<span data-ttu-id="8f50f-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-423">DateTime</span></span>|  
|<span data-ttu-id="8f50f-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8f50f-424">DATE_MODIFIED</span></span>|<span data-ttu-id="8f50f-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="8f50f-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="8f50f-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="8f50f-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-427">ColumnName</span></span>|<span data-ttu-id="8f50f-428">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8f50f-430">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-430">String</span></span>|  
|<span data-ttu-id="8f50f-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8f50f-432">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-432">String</span></span>|  
|<span data-ttu-id="8f50f-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="8f50f-434">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-434">String</span></span>|  
|<span data-ttu-id="8f50f-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-435">COLUMN_NAME</span></span>|<span data-ttu-id="8f50f-436">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-436">String</span></span>|  
|<span data-ttu-id="8f50f-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8f50f-437">COLUMN_GUID</span></span>|<span data-ttu-id="8f50f-438">Guid</span><span class="sxs-lookup"><span data-stu-id="8f50f-438">Guid</span></span>|  
|<span data-ttu-id="8f50f-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8f50f-439">COLUMN_PROPID</span></span>|<span data-ttu-id="8f50f-440">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-440">Int64</span></span>|  
|<span data-ttu-id="8f50f-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="8f50f-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="8f50f-442">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-442">Int64</span></span>|  
|<span data-ttu-id="8f50f-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="8f50f-444">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-444">Int64</span></span>|  
|<span data-ttu-id="8f50f-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8f50f-445">IS_NULLABLE</span></span>|<span data-ttu-id="8f50f-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-446">Boolean</span></span>|  
|<span data-ttu-id="8f50f-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-447">DATA_TYPE</span></span>|<span data-ttu-id="8f50f-448">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-448">Int32</span></span>|  
|<span data-ttu-id="8f50f-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="8f50f-449">TYPE_GUID</span></span>|<span data-ttu-id="8f50f-450">Guid</span><span class="sxs-lookup"><span data-stu-id="8f50f-450">Guid</span></span>|  
|<span data-ttu-id="8f50f-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8f50f-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8f50f-452">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-452">Int64</span></span>|  
|<span data-ttu-id="8f50f-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8f50f-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8f50f-454">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-454">Int64</span></span>|  
|<span data-ttu-id="8f50f-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8f50f-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8f50f-456">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-456">Int32</span></span>|  
|<span data-ttu-id="8f50f-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8f50f-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="8f50f-458">Int16</span><span class="sxs-lookup"><span data-stu-id="8f50f-458">Int16</span></span>|  
|<span data-ttu-id="8f50f-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-459">DESCRIPTION</span></span>|<span data-ttu-id="8f50f-460">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-460">String</span></span>|  
|<span data-ttu-id="8f50f-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="8f50f-461">OVERLOAD</span></span>|<span data-ttu-id="8f50f-462">Int16</span><span class="sxs-lookup"><span data-stu-id="8f50f-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="8f50f-463">檢視</span><span class="sxs-lookup"><span data-stu-id="8f50f-463">Views</span></span>  
  
|<span data-ttu-id="8f50f-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-464">ColumnName</span></span>|<span data-ttu-id="8f50f-465">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-466">TABLE_CATALOG</span></span>|<span data-ttu-id="8f50f-467">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-467">String</span></span>|  
|<span data-ttu-id="8f50f-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="8f50f-469">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-469">String</span></span>|  
|<span data-ttu-id="8f50f-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-470">TABLE_NAME</span></span>|<span data-ttu-id="8f50f-471">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-471">String</span></span>|  
|<span data-ttu-id="8f50f-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="8f50f-473">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-473">String</span></span>|  
|<span data-ttu-id="8f50f-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-474">CHECK_OPTION</span></span>|<span data-ttu-id="8f50f-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-475">Boolean</span></span>|  
|<span data-ttu-id="8f50f-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="8f50f-476">IS_UPDATABLE</span></span>|<span data-ttu-id="8f50f-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-477">Boolean</span></span>|  
|<span data-ttu-id="8f50f-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-478">DESCRIPTION</span></span>|<span data-ttu-id="8f50f-479">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-479">String</span></span>|  
|<span data-ttu-id="8f50f-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8f50f-480">DATE_CREATED</span></span>|<span data-ttu-id="8f50f-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-481">DateTime</span></span>|  
|<span data-ttu-id="8f50f-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8f50f-482">DATE_MODIFIED</span></span>|<span data-ttu-id="8f50f-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="8f50f-484">索引</span><span class="sxs-lookup"><span data-stu-id="8f50f-484">Indexes</span></span>  
  
|<span data-ttu-id="8f50f-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-485">ColumnName</span></span>|<span data-ttu-id="8f50f-486">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-487">TABLE_CATALOG</span></span>|<span data-ttu-id="8f50f-488">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-488">String</span></span>|  
|<span data-ttu-id="8f50f-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="8f50f-490">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-490">String</span></span>|  
|<span data-ttu-id="8f50f-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-491">TABLE_NAME</span></span>|<span data-ttu-id="8f50f-492">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-492">String</span></span>|  
|<span data-ttu-id="8f50f-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-493">INDEX_CATALOG</span></span>|<span data-ttu-id="8f50f-494">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-494">String</span></span>|  
|<span data-ttu-id="8f50f-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="8f50f-496">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-496">String</span></span>|  
|<span data-ttu-id="8f50f-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-497">INDEX_NAME</span></span>|<span data-ttu-id="8f50f-498">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-498">String</span></span>|  
|<span data-ttu-id="8f50f-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="8f50f-499">PRIMARY_KEY</span></span>|<span data-ttu-id="8f50f-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-500">Boolean</span></span>|  
|<span data-ttu-id="8f50f-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="8f50f-501">UNIQUE</span></span>|<span data-ttu-id="8f50f-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-502">Boolean</span></span>|  
|<span data-ttu-id="8f50f-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="8f50f-503">CLUSTERED</span></span>|<span data-ttu-id="8f50f-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-504">Boolean</span></span>|  
|<span data-ttu-id="8f50f-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-505">TYPE</span></span>|<span data-ttu-id="8f50f-506">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-506">Int32</span></span>|  
|<span data-ttu-id="8f50f-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="8f50f-507">FILL_FACTOR</span></span>|<span data-ttu-id="8f50f-508">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-508">Int32</span></span>|  
|<span data-ttu-id="8f50f-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="8f50f-509">INITIAL_SIZE</span></span>|<span data-ttu-id="8f50f-510">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-510">Int32</span></span>|  
|<span data-ttu-id="8f50f-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="8f50f-511">NULLS</span></span>|<span data-ttu-id="8f50f-512">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-512">Int32</span></span>|  
|<span data-ttu-id="8f50f-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="8f50f-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="8f50f-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-514">Boolean</span></span>|  
|<span data-ttu-id="8f50f-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="8f50f-515">AUTO_UPDATE</span></span>|<span data-ttu-id="8f50f-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-516">Boolean</span></span>|  
|<span data-ttu-id="8f50f-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="8f50f-517">NULL_COLLATION</span></span>|<span data-ttu-id="8f50f-518">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-518">Int32</span></span>|  
|<span data-ttu-id="8f50f-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="8f50f-520">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-520">Int64</span></span>|  
|<span data-ttu-id="8f50f-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-521">COLUMN_NAME</span></span>|<span data-ttu-id="8f50f-522">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-522">String</span></span>|  
|<span data-ttu-id="8f50f-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8f50f-523">COLUMN_GUID</span></span>|<span data-ttu-id="8f50f-524">Guid</span><span class="sxs-lookup"><span data-stu-id="8f50f-524">Guid</span></span>|  
|<span data-ttu-id="8f50f-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8f50f-525">COLUMN_PROPID</span></span>|<span data-ttu-id="8f50f-526">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-526">Int64</span></span>|  
|<span data-ttu-id="8f50f-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="8f50f-527">COLLATION</span></span>|<span data-ttu-id="8f50f-528">Int16</span><span class="sxs-lookup"><span data-stu-id="8f50f-528">Int16</span></span>|  
|<span data-ttu-id="8f50f-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="8f50f-529">CARDINALITY</span></span>|<span data-ttu-id="8f50f-530">Decimal</span><span class="sxs-lookup"><span data-stu-id="8f50f-530">Decimal</span></span>|  
|<span data-ttu-id="8f50f-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="8f50f-531">PAGES</span></span>|<span data-ttu-id="8f50f-532">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-532">Int32</span></span>|  
|<span data-ttu-id="8f50f-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-533">FILTER_CONDITION</span></span>|<span data-ttu-id="8f50f-534">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-534">String</span></span>|  
|<span data-ttu-id="8f50f-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="8f50f-535">INTEGRATED</span></span>|<span data-ttu-id="8f50f-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="8f50f-537">Microsoft Jet OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="8f50f-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="8f50f-538">除了通用結構描述集合之外，Microsoft Jet OLE DB 驅動程式還支援下列特定的結構描述集合：</span><span class="sxs-lookup"><span data-stu-id="8f50f-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
- <span data-ttu-id="8f50f-539">資料表</span><span class="sxs-lookup"><span data-stu-id="8f50f-539">Tables</span></span>  
  
- <span data-ttu-id="8f50f-540">資料行</span><span class="sxs-lookup"><span data-stu-id="8f50f-540">Columns</span></span>  
  
- <span data-ttu-id="8f50f-541">程序</span><span class="sxs-lookup"><span data-stu-id="8f50f-541">Procedures</span></span>  
  
- <span data-ttu-id="8f50f-542">檢視</span><span class="sxs-lookup"><span data-stu-id="8f50f-542">Views</span></span>  
  
- <span data-ttu-id="8f50f-543">索引</span><span class="sxs-lookup"><span data-stu-id="8f50f-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="8f50f-544">資料表</span><span class="sxs-lookup"><span data-stu-id="8f50f-544">Tables</span></span>  
  
|<span data-ttu-id="8f50f-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-545">ColumnName</span></span>|<span data-ttu-id="8f50f-546">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-547">TABLE_CATALOG</span></span>|<span data-ttu-id="8f50f-548">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-548">String</span></span>|  
|<span data-ttu-id="8f50f-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="8f50f-550">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-550">String</span></span>|  
|<span data-ttu-id="8f50f-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-551">TABLE_NAME</span></span>|<span data-ttu-id="8f50f-552">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-552">String</span></span>|  
|<span data-ttu-id="8f50f-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-553">TABLE_TYPE</span></span>|<span data-ttu-id="8f50f-554">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-554">String</span></span>|  
|<span data-ttu-id="8f50f-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="8f50f-555">TABLE_GUID</span></span>|<span data-ttu-id="8f50f-556">Guid</span><span class="sxs-lookup"><span data-stu-id="8f50f-556">Guid</span></span>|  
|<span data-ttu-id="8f50f-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-557">DESCRIPTION</span></span>|<span data-ttu-id="8f50f-558">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-558">String</span></span>|  
|<span data-ttu-id="8f50f-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="8f50f-559">TABLE_PROPID</span></span>|<span data-ttu-id="8f50f-560">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-560">Int64</span></span>|  
|<span data-ttu-id="8f50f-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8f50f-561">DATE_CREATED</span></span>|<span data-ttu-id="8f50f-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-562">DateTime</span></span>|  
|<span data-ttu-id="8f50f-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8f50f-563">DATE_MODIFIED</span></span>|<span data-ttu-id="8f50f-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="8f50f-565">資料行</span><span class="sxs-lookup"><span data-stu-id="8f50f-565">Columns</span></span>  
  
|<span data-ttu-id="8f50f-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-566">ColumnName</span></span>|<span data-ttu-id="8f50f-567">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-568">TABLE_CATALOG</span></span>|<span data-ttu-id="8f50f-569">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-569">String</span></span>|  
|<span data-ttu-id="8f50f-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="8f50f-571">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-571">String</span></span>|  
|<span data-ttu-id="8f50f-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-572">TABLE_NAME</span></span>|<span data-ttu-id="8f50f-573">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-573">String</span></span>|  
|<span data-ttu-id="8f50f-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-574">COLUMN_NAME</span></span>|<span data-ttu-id="8f50f-575">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-575">String</span></span>|  
|<span data-ttu-id="8f50f-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8f50f-576">COLUMN_GUID</span></span>|<span data-ttu-id="8f50f-577">Guid</span><span class="sxs-lookup"><span data-stu-id="8f50f-577">Guid</span></span>|  
|<span data-ttu-id="8f50f-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8f50f-578">COLUMN_PROPID</span></span>|<span data-ttu-id="8f50f-579">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-579">Int64</span></span>|  
|<span data-ttu-id="8f50f-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="8f50f-581">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-581">Int64</span></span>|  
|<span data-ttu-id="8f50f-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="8f50f-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="8f50f-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-583">Boolean</span></span>|  
|<span data-ttu-id="8f50f-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="8f50f-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="8f50f-585">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-585">String</span></span>|  
|<span data-ttu-id="8f50f-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="8f50f-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="8f50f-587">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-587">Int64</span></span>|  
|<span data-ttu-id="8f50f-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="8f50f-588">IS_NULLABLE</span></span>|<span data-ttu-id="8f50f-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-589">Boolean</span></span>|  
|<span data-ttu-id="8f50f-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-590">DATA_TYPE</span></span>|<span data-ttu-id="8f50f-591">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-591">Int32</span></span>|  
|<span data-ttu-id="8f50f-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="8f50f-592">TYPE_GUID</span></span>|<span data-ttu-id="8f50f-593">Guid</span><span class="sxs-lookup"><span data-stu-id="8f50f-593">Guid</span></span>|  
|<span data-ttu-id="8f50f-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8f50f-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="8f50f-595">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-595">Int64</span></span>|  
|<span data-ttu-id="8f50f-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="8f50f-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="8f50f-597">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-597">Int64</span></span>|  
|<span data-ttu-id="8f50f-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8f50f-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="8f50f-599">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-599">Int32</span></span>|  
|<span data-ttu-id="8f50f-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="8f50f-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="8f50f-601">Int16</span><span class="sxs-lookup"><span data-stu-id="8f50f-601">Int16</span></span>|  
|<span data-ttu-id="8f50f-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="8f50f-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="8f50f-603">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-603">Int64</span></span>|  
|<span data-ttu-id="8f50f-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="8f50f-605">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-605">String</span></span>|  
|<span data-ttu-id="8f50f-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="8f50f-607">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-607">String</span></span>|  
|<span data-ttu-id="8f50f-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="8f50f-609">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-609">String</span></span>|  
|<span data-ttu-id="8f50f-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="8f50f-611">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-611">String</span></span>|  
|<span data-ttu-id="8f50f-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="8f50f-613">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-613">String</span></span>|  
|<span data-ttu-id="8f50f-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-614">COLLATION_NAME</span></span>|<span data-ttu-id="8f50f-615">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-615">String</span></span>|  
|<span data-ttu-id="8f50f-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="8f50f-617">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-617">String</span></span>|  
|<span data-ttu-id="8f50f-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="8f50f-619">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-619">String</span></span>|  
|<span data-ttu-id="8f50f-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-620">DOMAIN_NAME</span></span>|<span data-ttu-id="8f50f-621">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-621">String</span></span>|  
|<span data-ttu-id="8f50f-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-622">DESCRIPTION</span></span>|<span data-ttu-id="8f50f-623">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="8f50f-624">程序</span><span class="sxs-lookup"><span data-stu-id="8f50f-624">Procedures</span></span>  
  
|<span data-ttu-id="8f50f-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-625">ColumnName</span></span>|<span data-ttu-id="8f50f-626">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="8f50f-628">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-628">String</span></span>|  
|<span data-ttu-id="8f50f-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="8f50f-630">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-630">String</span></span>|  
|<span data-ttu-id="8f50f-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="8f50f-632">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-632">String</span></span>|  
|<span data-ttu-id="8f50f-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="8f50f-634">Int16</span><span class="sxs-lookup"><span data-stu-id="8f50f-634">Int16</span></span>|  
|<span data-ttu-id="8f50f-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="8f50f-636">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-636">String</span></span>|  
|<span data-ttu-id="8f50f-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-637">DESCRIPTION</span></span>|<span data-ttu-id="8f50f-638">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-638">String</span></span>|  
|<span data-ttu-id="8f50f-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8f50f-639">DATE_CREATED</span></span>|<span data-ttu-id="8f50f-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-640">DateTime</span></span>|  
|<span data-ttu-id="8f50f-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8f50f-641">DATE_MODIFIED</span></span>|<span data-ttu-id="8f50f-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="8f50f-643">檢視</span><span class="sxs-lookup"><span data-stu-id="8f50f-643">Views</span></span>  
  
|<span data-ttu-id="8f50f-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-644">ColumnName</span></span>|<span data-ttu-id="8f50f-645">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-646">TABLE_CATALOG</span></span>|<span data-ttu-id="8f50f-647">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-647">String</span></span>|  
|<span data-ttu-id="8f50f-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="8f50f-649">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-649">String</span></span>|  
|<span data-ttu-id="8f50f-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-650">TABLE_NAME</span></span>|<span data-ttu-id="8f50f-651">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-651">String</span></span>|  
|<span data-ttu-id="8f50f-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="8f50f-653">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-653">String</span></span>|  
|<span data-ttu-id="8f50f-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-654">CHECK_OPTION</span></span>|<span data-ttu-id="8f50f-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-655">Boolean</span></span>|  
|<span data-ttu-id="8f50f-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="8f50f-656">IS_UPDATABLE</span></span>|<span data-ttu-id="8f50f-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-657">Boolean</span></span>|  
|<span data-ttu-id="8f50f-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="8f50f-658">DESCRIPTION</span></span>|<span data-ttu-id="8f50f-659">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-659">String</span></span>|  
|<span data-ttu-id="8f50f-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="8f50f-660">DATE_CREATED</span></span>|<span data-ttu-id="8f50f-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-661">DateTime</span></span>|  
|<span data-ttu-id="8f50f-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="8f50f-662">DATE_MODIFIED</span></span>|<span data-ttu-id="8f50f-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="8f50f-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="8f50f-664">索引</span><span class="sxs-lookup"><span data-stu-id="8f50f-664">Indexes</span></span>  
  
|<span data-ttu-id="8f50f-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="8f50f-665">ColumnName</span></span>|<span data-ttu-id="8f50f-666">DataType</span><span class="sxs-lookup"><span data-stu-id="8f50f-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="8f50f-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-667">TABLE_CATALOG</span></span>|<span data-ttu-id="8f50f-668">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-668">String</span></span>|  
|<span data-ttu-id="8f50f-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="8f50f-670">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-670">String</span></span>|  
|<span data-ttu-id="8f50f-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-671">TABLE_NAME</span></span>|<span data-ttu-id="8f50f-672">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-672">String</span></span>|  
|<span data-ttu-id="8f50f-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="8f50f-673">INDEX_CATALOG</span></span>|<span data-ttu-id="8f50f-674">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-674">String</span></span>|  
|<span data-ttu-id="8f50f-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="8f50f-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="8f50f-676">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-676">String</span></span>|  
|<span data-ttu-id="8f50f-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-677">INDEX_NAME</span></span>|<span data-ttu-id="8f50f-678">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-678">String</span></span>|  
|<span data-ttu-id="8f50f-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="8f50f-679">PRIMARY_KEY</span></span>|<span data-ttu-id="8f50f-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-680">Boolean</span></span>|  
|<span data-ttu-id="8f50f-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="8f50f-681">UNIQUE</span></span>|<span data-ttu-id="8f50f-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-682">Boolean</span></span>|  
|<span data-ttu-id="8f50f-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="8f50f-683">CLUSTERED</span></span>|<span data-ttu-id="8f50f-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-684">Boolean</span></span>|  
|<span data-ttu-id="8f50f-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="8f50f-685">TYPE</span></span>|<span data-ttu-id="8f50f-686">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-686">Int32</span></span>|  
|<span data-ttu-id="8f50f-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="8f50f-687">FILL_FACTOR</span></span>|<span data-ttu-id="8f50f-688">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-688">Int32</span></span>|  
|<span data-ttu-id="8f50f-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="8f50f-689">INITIAL_SIZE</span></span>|<span data-ttu-id="8f50f-690">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-690">Int32</span></span>|  
|<span data-ttu-id="8f50f-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="8f50f-691">NULLS</span></span>|<span data-ttu-id="8f50f-692">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-692">Int32</span></span>|  
|<span data-ttu-id="8f50f-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="8f50f-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="8f50f-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-694">Boolean</span></span>|  
|<span data-ttu-id="8f50f-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="8f50f-695">AUTO_UPDATE</span></span>|<span data-ttu-id="8f50f-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-696">Boolean</span></span>|  
|<span data-ttu-id="8f50f-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="8f50f-697">NULL_COLLATION</span></span>|<span data-ttu-id="8f50f-698">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-698">Int32</span></span>|  
|<span data-ttu-id="8f50f-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="8f50f-700">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-700">Int64</span></span>|  
|<span data-ttu-id="8f50f-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="8f50f-701">COLUMN_NAME</span></span>|<span data-ttu-id="8f50f-702">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-702">String</span></span>|  
|<span data-ttu-id="8f50f-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="8f50f-703">COLUMN_GUID</span></span>|<span data-ttu-id="8f50f-704">Guid</span><span class="sxs-lookup"><span data-stu-id="8f50f-704">Guid</span></span>|  
|<span data-ttu-id="8f50f-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="8f50f-705">COLUMN_PROPID</span></span>|<span data-ttu-id="8f50f-706">Int64</span><span class="sxs-lookup"><span data-stu-id="8f50f-706">Int64</span></span>|  
|<span data-ttu-id="8f50f-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="8f50f-707">COLLATION</span></span>|<span data-ttu-id="8f50f-708">Int16</span><span class="sxs-lookup"><span data-stu-id="8f50f-708">Int16</span></span>|  
|<span data-ttu-id="8f50f-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="8f50f-709">CARDINALITY</span></span>|<span data-ttu-id="8f50f-710">Decimal</span><span class="sxs-lookup"><span data-stu-id="8f50f-710">Decimal</span></span>|  
|<span data-ttu-id="8f50f-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="8f50f-711">PAGES</span></span>|<span data-ttu-id="8f50f-712">Int32</span><span class="sxs-lookup"><span data-stu-id="8f50f-712">Int32</span></span>|  
|<span data-ttu-id="8f50f-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="8f50f-713">FILTER_CONDITION</span></span>|<span data-ttu-id="8f50f-714">String</span><span class="sxs-lookup"><span data-stu-id="8f50f-714">String</span></span>|  
|<span data-ttu-id="8f50f-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="8f50f-715">INTEGRATED</span></span>|<span data-ttu-id="8f50f-716">Boolean</span><span class="sxs-lookup"><span data-stu-id="8f50f-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f50f-717">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8f50f-717">See also</span></span>

- [<span data-ttu-id="8f50f-718">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="8f50f-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
