

# migration
`import "./pkg/migration"`

* [Overview](#pkg-overview)
* [Index](#pkg-index)

## <a name="pkg-overview">Overview</a>



## <a name="pkg-index">Index</a>
* [func ReadDir(dir string, set *Set) error](#ReadDir)
* [type Migration](#Migration)
* [type Set](#Set)
  * [func NewSet(pg *pgx.ConnPool) *Set](#NewSet)
  * [func (s *Set) Add(service string, priority, version int, migration Migration)](#Set.Add)
  * [func (s *Set) Apply(name string, priority, minVersion int, isForced, noAutoOnly bool) (int, int, error)](#Set.Apply)
  * [func (s *Set) ApplyAll(force bool) (int, error)](#Set.ApplyAll)
  * [func (s *Set) BumpServiceVersion(name string, ver int) error](#Set.BumpServiceVersion)
  * [func (s *Set) ServiceExists(name string) bool](#Set.ServiceExists)
  * [func (s *Set) ServiceVersion(name string) (int, error)](#Set.ServiceVersion)


#### <a name="pkg-files">Package files</a>
[migration.go](https://golang.org/src//target/migration.go) [yaml.go](https://golang.org/src//target/yaml.go)





## <a name="ReadDir">func</a> [ReadDir](https://golang.org/src/./pkg/migration/yaml.go?s=768:808#L37)
``` go
func ReadDir(dir string, set *Set) error
```
ReadDir reads migrations from all yaml files in the dir.




## <a name="Migration">type</a> [Migration](https://golang.org/src/./pkg/migration/migration.go?s=133:213#L12)
``` go
type Migration struct {
    AllowError bool
    NoAuto     bool
    Queries    []string
}

```
Migration is a single migration.










## <a name="Set">type</a> [Set](https://golang.org/src/./pkg/migration/migration.go?s=263:359#L19)
``` go
type Set struct {
    sync.Mutex
    // contains filtered or unexported fields
}

```
Set is a set of migrations for all services.







### <a name="NewSet">func</a> [NewSet](https://golang.org/src/./pkg/migration/migration.go?s=400:434#L26)
``` go
func NewSet(pg *pgx.ConnPool) *Set
```
NewSet returns new instance of Set.





### <a name="Set.Add">func</a> (\*Set) [Add](https://golang.org/src/./pkg/migration/migration.go?s=808:885#L45)
``` go
func (s *Set) Add(service string, priority, version int, migration Migration)
```
Add adds migration to the set.




### <a name="Set.Apply">func</a> (\*Set) [Apply](https://golang.org/src/./pkg/migration/migration.go?s=3159:3262#L137)
``` go
func (s *Set) Apply(name string, priority, minVersion int, isForced, noAutoOnly bool) (int, int, error)
```
Apply applies migrations for specified service with version > minVersion.




### <a name="Set.ApplyAll">func</a> (\*Set) [ApplyAll](https://golang.org/src/./pkg/migration/migration.go?s=4092:4139#L172)
``` go
func (s *Set) ApplyAll(force bool) (int, error)
```
ApplyAll applies all migrations for all services.




### <a name="Set.BumpServiceVersion">func</a> (\*Set) [BumpServiceVersion](https://golang.org/src/./pkg/migration/migration.go?s=5112:5172#L205)
``` go
func (s *Set) BumpServiceVersion(name string, ver int) error
```
BumpServiceVersion updates service version.




### <a name="Set.ServiceExists">func</a> (\*Set) [ServiceExists](https://golang.org/src/./pkg/migration/migration.go?s=604:649#L35)
``` go
func (s *Set) ServiceExists(name string) bool
```
ServiceExists returns true if there are known migrations for service.




### <a name="Set.ServiceVersion">func</a> (\*Set) [ServiceVersion](https://golang.org/src/./pkg/migration/migration.go?s=5469:5523#L217)
``` go
func (s *Set) ServiceVersion(name string) (int, error)
```
ServiceVersion returns currently deployed version of the service.








- - -
Generated by [godoc2md](http://godoc.org/github.com/lanre-ade/godoc2md)