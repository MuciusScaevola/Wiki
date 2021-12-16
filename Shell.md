Shellsort is a simple extension of insertion sort that gains speed by allowing exchanges of elements that are far apart.
In other words consider the file as composed of subfiles of the elements (as example) 0-4-8-12, 1-5-9-13, 2-6-10-14, 3-7-11 ans sort each of the subfiles.

```c
void shell_sort(Item a[], int l, int r)
{
    int i, j, h;
    
    for(h = 1; h <= (r - l) / 9; h = 3 * h + 1);    // Put h in position
    for(; h > 0; h /= 3)                            
    {
        for(i = l + h; i <= r; i++)
        {
            j = i;
            Item v = a[i];
            
            while(j >= l + h && less(v, a[j - h]))
            {
                a[j] = a[j - h];
                j -= h;
            }
            a[j] = v;
        }
    }
}
```
