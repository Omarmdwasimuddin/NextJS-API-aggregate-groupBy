## NextJS API---> Aggregate & GroupBy

### heading...
![](https://imgur.com/cpc9gg2.png)

```bash
import prisma from "@/lib/prisma";
import { NextRequest, NextResponse } from "next/server";


export async function GET(request: NextRequest) {
    try {
        
        const readData = await prisma.employee.aggregate({
            _count: {
                id: true,
            },
            _sum: {
                salary: true,
            },
            _avg: {
                salary: true,
            },
            _min: {
                salary: true,
            },
            _max: {
                salary: true,
            }
        });

        return NextResponse.json(
            {status: "success", message: "Read data successfully", data: readData},
            {status: 200}
        )
    } catch (error) {
        return NextResponse.json(
            {status: "failed", message: "Internal server problem"},
            {status: 500}
        )
    }
}
```
---

### heading...
![](https://imgur.com/GcmdD8E.png)

```bash
const readData = await prisma.employee.groupBy({
            by: ['city'],
        });
```
---

### heading...
![](https://imgur.com/7s5lPny.png)

```bash
const readData = await prisma.employee.groupBy({
            by: ['city'],
            _count: {
                id: true,
            }
        });
```
---

### heading...
![](https://imgur.com/IWyKhHq.png)

```bash
const readData = await prisma.employee.groupBy({
            by: ['city'],
            _sum: {
                salary: true,
            }
        });
```
---
