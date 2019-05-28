using System;
using System.Collections;
using System.Collections.Generic;
using System.IO;
using UnityEngine;

public class ApkValidater
{


    //todo string 최적화 하기 . 
    public static string GetData()
    {
        string result = "";

        if (Application.platform == RuntimePlatform.Android)
        {
            var osBuild = new AndroidJavaClass("android.os.Build");
            string brand = osBuild.GetStatic<string>("BRAND");
            string fingerPrint = osBuild.GetStatic<string>("FINGERPRINT");
            string model = osBuild.GetStatic<string>("MODEL");
            string menufacturer = osBuild.GetStatic<string>("MANUFACTURER");
            string device = osBuild.GetStatic<string>("DEVICE");
            string product = osBuild.GetStatic<string>("PRODUCT");

            result += Application.installerName;
            result += "/";
            result += Application.installMode.ToString();
            result += "/";
            result += Application.buildGUID;
            result += "/";
            result += "Genuine :" + Application.genuine;
            result += "/";
            result += "Rooted : " + isRooted();
            result += "/";
            result += "Emulator : " + IsEmulator();
            result += "/";
            result += "Model : " + model;
            result += "/";
            result += "Menufacturer : " + menufacturer;
            result += "/";
            result += "Device : " + device;
            result += "/";
            result += "Fingerprint : " + fingerPrint;
            result += "/";
            result += "Product : " + product;
        }
        else
        {
            result += Application.installerName;
            result += "/";
            result += Application.installMode.ToString();
            result += "/";
            result += Application.buildGUID;
            result += "/";
            result += "Genuine :" + Application.genuine;
            result += "/";
        }
        return result;
    }


    public static bool isRooted()
    {
        bool isRoot = false;

        if (Application.platform == RuntimePlatform.Android)
        {
            if (isRootedPrivate("/system/bin/su"))
                isRoot = true;
            if (isRootedPrivate("/system/xbin/su"))
                isRoot = true;
            if (isRootedPrivate("/system/app/SuperUser.apk"))
                isRoot = true;
            if (isRootedPrivate("/data/data/com.noshufou.android.su"))
                isRoot = true;
            if (isRootedPrivate("/sbin/su"))
                isRoot = true;
        }
     
        return isRoot;
    }
    public static bool IsEmulator()
    {
        if (Application.platform == RuntimePlatform.Android)
        {
            AndroidJavaClass osBuild;
        osBuild = new AndroidJavaClass("android.os.Build");
        string fingerPrint = osBuild.GetStatic<string>("FINGERPRINT");
        string model = osBuild.GetStatic<string>("MODEL");
        string menufacturer = osBuild.GetStatic<string>("MANUFACTURER");
        string brand = osBuild.GetStatic<string>("BRAND");
        string device = osBuild.GetStatic<string>("DEVICE");
        string product = osBuild.GetStatic<string>("PRODUCT");

        return fingerPrint.Contains("generic")
                || fingerPrint.Contains("unknown")
                  || model.Contains("google_sdk")
                || model.Contains("Emulator")
               || model.Contains("Android SDK built for x86")
          || menufacturer.Contains("Genymotion")
            || (brand.Contains("generic") && device.Contains("generic"))
    || product.Equals("google_sdk")
            || product.Equals("unknown");

        }
        if (Application.platform == RuntimePlatform.OSXEditor)
        {
            return true;
        }
        return false;
    }

    public static bool isRootedPrivate(string path)
    {
        bool boolTemp = false;

        if (File.Exists(path))
        {
            boolTemp = true;
        }

        return boolTemp;
    }
}
