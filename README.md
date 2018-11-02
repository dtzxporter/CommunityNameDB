# CommunityNameDB
A list of asset names identified by the lovely community members

Please see: [Specification](https://github.com/dtzxporter/CommunityNameDB/blob/master/spec.md) before submitting your names, they will need to conform to it first. Don't bother using the GIT client, just file an Issue and someone will add them for you!

To generate a test database locally, download [DBGenerator](https://mega.nz/#!tZ5THDKY!jQdvzawOYyLvP3n0Gx9g8PpkwsvFMWjEV9zYt004_70) and add the names to the corrosponding text file per asset type, one per line, then run the program. Copy the resulting *.wni files to the `package_index` folder and reload the assets.

The following is the hash algorithm for BO4

```cpp
const int64_t FNVPrime = 0x100000001B3;
const int64_t FNVOffset = 0xCBF29CE484222325;

int64_t Hash(const char* Data, uint64_t Size)
{
    int64_t Result = FNVOffset;

    for (uint64_t i = 0; i < Size; i++)
    {
        Result ^= Data[i];
        Result *= FNVPrime;
    }

    return (Result & 0x7FFFFFFFFFFFFFFF);   // Mask off bit
}

auto Example = Hash("void", strlen("void"));
```
