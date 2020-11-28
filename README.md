# Challenge-3---Create-a-real-scala-spark-project

SBT & Scala setup for IntelliJ

Pre-requisite: Java 8 is installed

Open IntelliJ > File > Settings > Plugins > 
Search and install the Scala Plugin

 

Create new project with Scala & sbt
 

 
Specify versions
You should specify the java version 8.
Scala version can be the latest. I specified 2.11.11
 

As soon as you click on Finish you the IDE will start syncing to download the associated SBT jars
 

When the build is finished the sbt specific jars would have been downloaded
 

Open build.sbt
 

Add the following content

scalaVersion := "2.11.11"

val sparkVersion = "2.2.0"

libraryDependencies ++= Seq(
  "org.apache.spark" %% "spark-core" % sparkVersion,
  "org.apache.spark" %% "spark-sql" % sparkVersion
)

As soon as you add this content, a dialog will appear at the bottom right to ‘Import changes’, click on it.
 
After the build is finished you should be able to see the spark jars. Your imports should work now!

Test the config
Create a new Scala class… the imports will now be resolved.
 

import org.apache.spark.sql.{SparkSession}

object Test {

  def main(args: Array[String]): Unit = {
    val spark: SparkSession = SparkSession
      .builder()
      .master("local[3]")
      .appName("SparkByExample")
      .getOrCreate()

    println(spark.version)

  }
}







