
#Tables
"use client";

import * as React from "react";
import {
  ColumnDef,
  ColumnFiltersState,
  SortingState,
  VisibilityState,
  flexRender,
  getCoreRowModel,
  getFilteredRowModel,
  getPaginationRowModel,
  getSortedRowModel,
  useReactTable,
} from "@tanstack/react-table";
import { ArrowUpDown, ChevronDown, MoreHorizontal } from "lucide-react";

import { Button } from "@/components/ui/button";
import { Checkbox } from "@/components/ui/checkbox";
import {
  DropdownMenu,
  DropdownMenuCheckboxItem,
  DropdownMenuContent,
  DropdownMenuItem,
  DropdownMenuLabel,
  DropdownMenuSeparator,
  DropdownMenuTrigger,
} from "@/components/ui/dropdown-menu";
import { Input } from "@/components/ui/input";
import {
  Table,
  TableBody,
  TableCell,
  TableHead,
  TableHeader,
  TableRow,
} from "@/components/ui/table";

const data: Payment[] = [
  {
    id: "1",
    Name: "Adobe Photoshop",
    version: "16.0.4266.1003",
    size: "2.3GB",
    published: "25 Feb 2025",
    status: "Active",
    os: "Mac",
    downloadCount: 1300,
    installationSuccess: 1250,
    bundleConversion: 1200,
    successRate: "92%",
  },
  {
    id: "2",
    Name: "Microsoft Office",
    version: "2019",
    size: "3.8GB",
    published: "12 Mar 2024",
    status: "Active",
    os: "Windows",
    downloadCount: 2100,
    installationSuccess: 2050,
    bundleConversion: 2000,
    successRate: "95%",
  },
  {
    id: "4",
    Name: "Slack",
    version: "4.16.2",
    size: "92MB",
    published: "02 Jun 2026",
    status: "Inactive",
    os: "Windows",
    downloadCount: 1900,
    installationSuccess: 1850,
    bundleConversion: 1800,
    successRate: "95%",
  },
  {
    id: "5",
    Name: "Capcut",
    version: "42.1.6.22",
    size: "512MB",
    published: "10 Jun 2023",
    status: "Active",
    os: "Mac",
    downloadCount: 800,
    installationSuccess: 750,
    bundleConversion: 700,
    successRate: "88%",
  },
  {
    id: "6",
    Name: "Cyberlink YouCam",
    version: "10.1.4203.0",
    size: "379MB",
    published: "10 Feb 2025",
    status: "Inactive",
    os: "Windows",
    downloadCount: 2800,
    installationSuccess: 2750,
    bundleConversion: 2700,
    successRate: "97%",
  },
  {
    id: "7",
    Name: "ApowerREC",
    version: "1.7.1.8",
    size: "57.5MB",
    published: "23 Jan 2025",
    status: "Active",
    os: "Windows",
    downloadCount: 1400,
    installationSuccess: 1350,
    bundleConversion: 1300,
    successRate: "92%",
  },
  {
    id: "8",
    Name: "Adobe Animate 2024",
    version: "24.0.4.28",
    size: "2.96GB",
    published: "22 Dec 2025",
    status: "Inactive",
    os: "Mac",
    downloadCount: 1700,
    installationSuccess: 1650,
    bundleConversion: 1600,
    successRate: "94%",
  },
  {
    id: "9",
    Name: "DaVinci Resolve Studio",
    version: "19.0.0.43",
    size: "4.86GB",
    published: "23 Sep 2025",
    status: "Inactive",
    os: "Windows",
    downloadCount: 1100,
    installationSuccess: 1050,
    bundleConversion: 1000,
    successRate: "91%",
  },
  {
    id: "10",
    Name: "Wondershare PDFelement Pro",
    version: "10.4.6.2777",
    size: "179MB",
    os: "Windows",
    published: "16 Nov 2025",
    status: "Active",
    downloadCount: 900,
    installationSuccess: 850,
    bundleConversion: 800,
    successRate: "89%",
  },
  {
    id: "11",
    Name: "Adobe Photoshop",
    version: "16.0.4266.1003",
    size: "2.3GB",
    published: "25 Feb 2025",
    status: "Active",
    os: "Mac",
    downloadCount: 3200,
    installationSuccess: 3100,
    bundleConversion: 3000,
    successRate: "94%",
  },
  {
    id: "12",
    Name: "Microsoft Office",
    version: "2019",
    size: "3.8GB",
    published: "12 Mar 2024",
    status: "Active",
    os: "Mac",
    downloadCount: 5000,
    installationSuccess: 4900,
    bundleConversion: 4800,
    successRate: "98%",
  },
  {
    id: "14",
    Name: "Slack",
    version: "4.16.2",
    size: "92MB",
    published: "02 Jun 2026",
    status: "Inactive",
    os: "Mac",
    downloadCount: 2200,
    installationSuccess: 2150,
    bundleConversion: 2100,
    successRate: "95%",
  },
  {
    id: "15",
    Name: "Capcut",
    version: "42.1.6.22",
    size: "512MB",
    os: "Mac",
    published: "10 Jun 2023",
    status: "Active",
    downloadCount: 1300,
    installationSuccess: 1250,
    bundleConversion: 1200,
    successRate: "93%",
  },
  {
    id: "16",
    Name: "Cyberlink YouCam",
    version: "10.1.4203.0",
    size: "379MB",
    published: "10 Feb 2025",
    status: "Inactive",
    os: "Windows",
    downloadCount: 1800,
    installationSuccess: 1750,
    bundleConversion: 1700,
    successRate: "94%",
  },
  {
    id: "17",
    Name: "ApowerREC",
    version: "1.7.1.8",
    size: "57.5MB",
    os: "Windows",
    published: "23 Jan 2025",
    status: "Active",
    downloadCount: 1200,
    installationSuccess: 1150,
    bundleConversion: 1100,
    successRate: "92%",
  },
  {
    id: "18",
    Name: "Adobe Animate 2024",
    version: "24.0.4.28",
    size: "2.96GB",
    published: "22 Dec 2025",
    status: "Inactive",
    os: "Windows",
    downloadCount: 3000,
    installationSuccess: 2900,
    bundleConversion: 2800,
    successRate: "95%",
  },
  {
    id: "19",
    Name: "DaVinci Resolve Studio",
    version: "19.0.0.43",
    size: "4.86GB",
    published: "23 Sep 2025",
    status: "Inactive",
    os: "Windows",
    downloadCount: 2500,
    installationSuccess: 2400,
    bundleConversion: 2300,
    successRate: "92%",
  },
  {
    id: "20",
    Name: "Wondershare PDFelement Pro",
    version: "10.4.6.2777",
    size: "179MB",
    os: "Windows",
    published: "16 Nov 2025",
    status: "Active",
    downloadCount: 1500,
    installationSuccess: 1400,
    bundleConversion: 1300,
    successRate: "93%",
  },
];

export type Payment = {
  id: string;
  successRate: string;
  downloadCount: number;
  status: string;
  Name: string;
  version: string;
  size: string;
  os: string;
  published: string;
  installationSuccess: number;
  bundleConversion: number;
};

export const columns: ColumnDef<Payment>[] = [
  {
    id: "select",
    header: ({ table }) => (
      <Checkbox
        checked={
          table.getIsAllPageRowsSelected() ||
          (table.getIsSomePageRowsSelected() && "indeterminate")
        }
        onCheckedChange={(value) => table.toggleAllPageRowsSelected(!!value)}
        aria-label='Select all'
      />
    ),
    cell: ({ row }) => (
      <Checkbox
        checked={row.getIsSelected()}
        onCheckedChange={(value) => row.toggleSelected(!!value)}
        aria-label='Select row'
      />
    ),
    enableSorting: false,
    enableHiding: false,
  },
  {
    accessorKey: "Name",
    header: "Name",
    cell: ({ row }) => <div className='capitalize'>{row.getValue("Name")}</div>,
  },
  {
    id: "actions",
    enableHiding: false,
    cell: ({ row }) => {
      const payment = row.original;

      return (
        <DropdownMenu>
          <DropdownMenuTrigger asChild>
            <Button variant='ghost' className='h-8 w-8 p-0'>
              <span className='sr-only'>Open menu</span>
              <MoreHorizontal className='h-4 w-4' />
            </Button>
          </DropdownMenuTrigger>
          <DropdownMenuContent align='end'>
            <DropdownMenuLabel>Actions</DropdownMenuLabel>
            <DropdownMenuItem
              onClick={() => navigator.clipboard.writeText(payment.id)}
            >
              Copy payment ID
            </DropdownMenuItem>
            <DropdownMenuSeparator />
            <DropdownMenuItem>View customer</DropdownMenuItem>
            <DropdownMenuItem>View payment details</DropdownMenuItem>
          </DropdownMenuContent>
        </DropdownMenu>
      );
    },
  },
  {
    accessorKey: "version",
    header: () => <div>Version</div>,

    cell: ({ row }) => (
      <div className='lowercase'>{row.getValue("version")}</div>
    ),
  },
  {
    accessorKey: "size",
    header: () => <div>Size</div>,

    cell: ({ row }) => <div className='lowercase'>{row.getValue("size")}</div>,
  },
  {
    accessorKey: "published",
    header: () => <div>Publish Date</div>,

    cell: ({ row }) => (
      <div className='lowercase'>{row.getValue("published")}</div>
    ),
  },
  {
    accessorKey: "status",
    header: () => <div>Status</div>,

    cell: ({ row }) => (
      <div className='lowercase'>{row.getValue("status")}</div>
    ),
  },
];

export function Tables() {
  const [sorting, setSorting] = React.useState<SortingState>([]);
  const [columnFilters, setColumnFilters] = React.useState<ColumnFiltersState>(
    []
  );
  const [columnVisibility, setColumnVisibility] =
    React.useState<VisibilityState>({});
  const [rowSelection, setRowSelection] = React.useState({});

  const table = useReactTable({
    data,
    columns,
    onSortingChange: setSorting,
    onColumnFiltersChange: setColumnFilters,
    getCoreRowModel: getCoreRowModel(),
    getPaginationRowModel: getPaginationRowModel(),
    getSortedRowModel: getSortedRowModel(),
    getFilteredRowModel: getFilteredRowModel(),
    onColumnVisibilityChange: setColumnVisibility,
    onRowSelectionChange: setRowSelection,
    state: {
      sorting,
      columnFilters,
      columnVisibility,
      rowSelection,
    },
  });

  return (
    <div className='w-full'>
      <div className='flex items-center py-4'>
        <Input
          placeholder='Filter emails...'
          value={(table.getColumn("email")?.getFilterValue() as string) ?? ""}
          onChange={(event) =>
            table.getColumn("email")?.setFilterValue(event.target.value)
          }
          className='max-w-sm'
        />
        <DropdownMenu>
          <DropdownMenuTrigger asChild>
            <Button variant='outline' className='ml-auto'>
              Columns <ChevronDown className='ml-2 h-4 w-4' />
            </Button>
          </DropdownMenuTrigger>
          <DropdownMenuContent align='end'>
            {table
              .getAllColumns()
              .filter((column) => column.getCanHide())
              .map((column) => {
                return (
                  <DropdownMenuCheckboxItem
                    key={column.id}
                    className='capitalize'
                    checked={column.getIsVisible()}
                    onCheckedChange={(value) =>
                      column.toggleVisibility(!!value)
                    }
                  >
                    {column.id}
                  </DropdownMenuCheckboxItem>
                );
              })}
          </DropdownMenuContent>
        </DropdownMenu>
      </div>
      <div className='rounded-md border'>
        <Table>
          <TableHeader>
            {table.getHeaderGroups().map((headerGroup) => (
              <TableRow key={headerGroup.id}>
                {headerGroup.headers.map((header) => {
                  return (
                    <TableHead key={header.id}>
                      {header.isPlaceholder
                        ? null
                        : flexRender(
                            header.column.columnDef.header,
                            header.getContext()
                          )}
                    </TableHead>
                  );
                })}
              </TableRow>
            ))}
          </TableHeader>
          <TableBody>
            {table.getRowModel().rows?.length ? (
              table.getRowModel().rows.map((row) => (
                <TableRow
                  key={row.id}
                  data-state={row.getIsSelected() && "selected"}
                >
                  {row.getVisibleCells().map((cell) => (
                    <TableCell key={cell.id}>
                      {flexRender(
                        cell.column.columnDef.cell,
                        cell.getContext()
                      )}
                    </TableCell>
                  ))}
                </TableRow>
              ))
            ) : (
              <TableRow>
                <TableCell
                  colSpan={columns.length}
                  className='h-24 text-center'
                >
                  No results.
                </TableCell>
              </TableRow>
            )}
          </TableBody>
        </Table>
      </div>
      <div className='flex items-center justify-end space-x-2 py-4'>
        <div className='flex-1 text-sm text-muted-foreground'>
          {table.getFilteredSelectedRowModel().rows.length} of{" "}
          {table.getFilteredRowModel().rows.length} row(s) selected.
        </div>
        <div className='space-x-2'>
          <Button
            variant='outline'
            size='sm'
            onClick={() => table.previousPage()}
            disabled={!table.getCanPreviousPage()}
          >
            Previous
          </Button>
          <Button
            variant='outline'
            size='sm'
            onClick={() => table.nextPage()}
            disabled={!table.getCanNextPage()}
          >
            Next
          </Button>
        </div>
      </div>
    </div>
  );
}
