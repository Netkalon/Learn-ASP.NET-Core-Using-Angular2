Introduction

In this article, we will learn ASP.NET Core Using Angular 2 in Visual studio 2017

Why should we use Angular 2?
Why should we use ASP.NET Core?
What should we know about?
How do we use Angular 2 in ASP.NET Core?
Why should we use Angular 2?

ASP.NET Core

Angular 2 is making the most of the new browser developments for creating better applications and Angular 2 is a complete rewrite of the Angular 1 framework. Angular 2 can build applications that live on

Web
Mobile
Desktop

ASP.NET Core
Each application consists of components. So component is a logical boundary of functionality for the application. It needs to have layered services, which are used to share the functionality. It will share the following

Template
Class
Metadata
Why should we use ASP.NET Core?

ASP.NET Core

Asp.net is a new open source and cross-platform framework for building modern cloud-based application, such as web apps, IoT apps and mobile backends.it was architected to provide an optimized development framework for apps that are deployed to the cloud.

You develop and run ASP.Net Core apps on

Windows
Mac
Linux

ASP.NET Core
ASP.Net Core is designed to integrate seamlessly with a variety of client-side framework, such as

AngularJS
KnockoutJS
Bootstrap
What should we know about?

Before you start Angular 2 & ASP.NET Core let's just refresh these things
ASP.NET Core
TypeScript

Angular 2 writes only in TS files. Typescript is a superset of java script developed and maintain by Microsoft. Typescript files are convert source code into another source language. This is one of the main features of most of browser supporting language of ECMA Script & developer can use Data type for variables.

Grunt JS Task Runner

Grunt is Java script task runner which can be used a command line tool for java script object & it is a task manager written on top of node JS. Grunt includes built in tasks that expand the functionality of your plugin and script & you can automate anything with less effort.

Angular 2

Angular 2 is different from Angular 1 but if you know Angular 1 it's a little bit easier to understand the code. If you want to know about Angular 1 and its advantages please visit my previous article.

ASP.NET Core MVC

You can create well-factored and testable web apps that follow the model-view-controller (MVC) pattern. Building Web APIs & Restful apps that reach a broad range of clients, including browser & Mobile

Features

Build Web UI & Web API
Support modern client side framework
Cloud-ready environment
Build dependency injection
Using NuGet Packages
Open source
Cross platform support (Windows, Mac, Linux)
How to use angular 2 in ASP.NET Core?

If you need the below software for installation, click on the above & download it.

Prerequisites

Visual studio 2017
Node JS
Open Visual Studio 2017

ASP.NET Core

Go to New menu >Click New & project. Now it will open New Project Window

ASP.NET Core

You can select ASP.NET Core Web Application on Framework 4.6. Enter the name of project in “Solution name” textbox then click ok button.

ASP.NET Core

Select web application & click “OK” button

ASP.NET Core

After scaffolds solution explorer looks like above picture, then if you click on PLAY button or IIS Express, you can see the base application of ASP.NET Core.

ASP.NET Core

Now application is ready for configuration, so let’s start.

Right click above the project Add> New item

ASP.NET Core

It will open a popup as add new items. You can find “npm Configuration File” for ASP.NET Core.

ASP.NET Core

After adding “package.json “clean the inside code and copy & paste the below given code.

JSON

{  
  "version": "1.0.0",  
  "name": "asp.net",  
  "private": true,  
  "devDependencies": {  
    "@angular/common": "^2.3.1",  
    "@angular/compiler": "^2.3.1",  
    "@angular/core": "^2.3.1",  
    "@angular/forms": "^2.3.1",  
    "@angular/http": "^2.3.1",  
    "@angular/platform-browser": "^2.3.1",  
    "@angular/platform-browser-dynamic": "^2.3.1",  
    "@angular/router": "^3.3.1",  
    "es6-shim": "^0.35.0",  
    "core-js": "^2.4.1",  
    "reflect-metadata": "^0.1.3",  
    "rxjs": "5.0.0-beta.12",  
    "systemjs": "0.19.27",  
    "zone.js": "^0.6.23",  
    "angular2-in-memory-web-api": "0.0.20",  
    "body-parser": "1.14.1",  
    "bootstrap": "3.3.5",  
    "jquery": "2.1.4"  
  },  
  "dependencies": {  
    "del": "2.1.0",  
    "gulp": "3.9.0",  
    "gulp-typescript": "^2.13.4",  
    "gulp-watch": "4.3.5",  
    "merge": "1.2.0",  
    "typescript": "^2.0.2",  
    "typings": "^1.3.3",  
    "rimraf": "^2.5.4"  
  },  
  "scripts": {  
    "postinstall": "typings install"  
  }  
}    
Again you can find “TypeScript JSON Configuration File” for ASP.NET Core.

ASP.NET Core

After adding “tsconfig.json “clean the inside code and copy & paste the below given code

JSON

{  
  "compileOnSave": true,  
  "compilerOptions": {  
  
    "target": "es5",  
    "module": "commonjs",  
    "moduleResolution": "node",  
    "sourceMap": true,  
    "emitDecoratorMetadata": true,  
    "experimentalDecorators": true,  
    "removeComments": false,  
    "noImplicitAny": true,  
    "suppressImplicitAnyIndexErrors": true  
  },  
  "exclude": [  
    "node_modules",  
    "wwwroot"  
  ]  
}  
Right click the project Add> New item>find JSON File & rename it as typings.json

ASP.NET Core

Add the below code in typings.json.

JSON

{  
  "globalDependencies": {  
    "core-js": "registry:dt/core-js#0.9.0+20170324193834",  
    "node": "registry:dt/node#6.0.0+20161110151007"  
  }  
}  
So the above three files are more important for Angular 2 configurations. Then right click on package.json & click to Restore Packages. Just confirm all the files are installed in NPM

ASP.NET Core

Right click the project & select Edit your project .csproj file.

ASP.NET Core

Add the below commend in this file

<TypeScriptCompileBlocked>true</TypeScriptCompileBlocked>  
 

Open the package manager console and Run the those lines

ASP.NET Core

You can create gulpfile.js using java script then cope & paste the given below code.

Java Script

var gulp = require('gulp');    
    
gulp.task('thirdparty', function ()    
{    
    gulp.src('./node_modules/core-js/**/*.js')    
        .pipe(gulp.dest('./wwwroot/node_modules/core-js'));    
    
    gulp.src('./node_modules/@angular/**/*.js')    
        .pipe(gulp.dest('./wwwroot/node_modules/@angular'));    
    
    gulp.src('./node_modules/zone.js/**/*.js')    
        .pipe(gulp.dest('./wwwroot/node_modules/zone.js'));    
    
    gulp.src('./node_modules/systemjs/**/*.js')    
        .pipe(gulp.dest('./wwwroot/node_modules/systemjs'));    
    
    gulp.src('./node_modules/reflect-metadata/**/*.js')    
        .pipe(gulp.dest('./wwwroot/node_modules/reflect-metadata'));    
    
    gulp.src('./node_modules/rxjs/**/*.js')    
        .pipe(gulp.dest('./wwwroot/node_modules/rxjs'));    
    
});    
gulp.task('copy', function ()    
{    
    gulp.src('./app/**/*.*')    
        .pipe(gulp.dest('./wwwroot/app'));    
});    
    
gulp.task('watch', function ()    
{    
    gulp.watch('./app/**/*.*', ['copy']);    
});  
Right click on this gulpfile.js & open task Runner Explorer

ASP.NET Core

Refresh the bottom screen then tasks will be loaded & right click on it and run it.

ASP.NET Core

Right click on “wwwroot” & create java script file & rename it as systemjs.config.js & put inside below the code.

Java Script

(function (global) {  
    // map tells the System loader where to look for things    
    var map = {  
        'app': 'app', // 'dist',    
        '@angular': 'node_modules/@angular',  
        'rxjs': 'node_modules/rxjs'  
    };  
    // packages tells the System loader how to load when no filename and/or no extension    
    var packages = {  
        'app': { main: 'main.js', defaultExtension: 'js' },  
        'rxjs': { defaultExtension: 'js' }  
    };  
    var ngPackageNames = [  
        'common',  
        'compiler',  
        'core',  
        'forms',  
        'http',  
        'platform-browser',  
        'platform-browser-dynamic',  
        'router'  
    ];  
    // Individual files (~300 requests):    
    function packIndex(pkgName) {  
        packages['@angular/' + pkgName] = { main: 'index.js', defaultExtension: 'js' };  
    }  
    // Bundled (~40 requests):    
    function packUmd(pkgName) {  
        packages['@angular/' + pkgName] = { main: '/bundles/' + pkgName + '.umd.js', defaultExtension: 'js' };  
    }  
    // Most environments should use UMD; some (Karma) need the individual index files    
    var setPackageConfig = System.packageWithIndex ? packIndex : packUmd;  
    // Add package entries for angular packages    
    ngPackageNames.forEach(setPackageConfig);  
    var config = {  
        map: map,  
        packages: packages  
    };  
    System.config(config);  
})(this);   
Just copy & paste the tsconfig.json file. You are almost over the configuration part. So let’s start writing Angular 2 code. Create new folder inside the “wwwroot” and create TS files

component.ts
module.ts
ts
After creating the above files, write code like below.

Type Script

app.component.ts

import { Component } from '@angular/core'    
@Component({    
    selector: 'app-loader',    
    template: `    
<div>     
<div>    
 <h4>Welcome to Angular with ASP.NET Core and Visual Studio 2017</h4>  
</div></div>  
`    
})    
export class AppComponent{}   
app.module.ts

import { NgModule } from "@angular/core";    
import { BrowserModule } from "@angular/platform-browser";    
import { AppComponent } from "../app/app.component";    
@NgModule({    
    imports: [BrowserModule],    
    declarations: [AppComponent],    
    bootstrap: [AppComponent]    
})    
export class AppModule { }   
main.ts 

import { platformBrowserDynamic } from "@angular/platform-browser-dynamic";  
import { AppModule } from "./app.module";  
platformBrowserDynamic().bootstrapModule(AppModule);   
Open _Layout.cshtml in views>Shared follow the below code inside the head tag. 

<script src="../node_modules/core-js/client/shim.min.js"></script>  
    <script src="../node_modules/zone.js/dist/zone.js"></script>  
    <script src="../node_modules/reflect-metadata/Reflect.js"></script>  
    <script src="../node_modules/systemjs/dist/system.src.js"></script>  
    <script src="../systemjs.config.js"></script>  
  
    <script>  
  
        System.import('app')  
            .then(  
            function () { console.log('started application'); },  
            function (err) { console.log('error starting application'); console.log(err); });  
    </script>   
Open index.cshtml in Views>Home write this line.

<app-loader>Loading...</app-loader>  
 

Now you can run the application & see our first angular 2 page in ASP.NET Core.

Output 1

ASP.NET Core

Output 2

ASP.NET Core

Download Source Here

Conclusion

In this article, we have learned about  ASP.NET Core Using Angular 2. If you have any queries, please tell me through the comments section, because your comments are very valuable.

Happy Coding!...
