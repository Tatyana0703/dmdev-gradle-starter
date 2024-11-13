содержимое settings.gradle

rootProject.name = 'gradle-starter'

include 'database'
include 'service'
include 'web'
include 'common'
include 'common:core'
include 'common:util'


вызов задачи для конкретного проекта
gradle :<имя проекта>:assemble
gradle :database:assemble
