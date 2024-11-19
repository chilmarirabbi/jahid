#jahid

import org.json.JSONArray;
import org.json.JSONObject;

public class DeviceVerifier {
    public static void main(String[] args) {
        // JSON ডাটা
        String jsonString = "{\"verified_devices\": [\"c41e398485531f31\", \"123456789abcdef0\", \"abcdef1234567890\"]}";
        
        // JSON পার্সিং
        JSONObject jsonData = new JSONObject(jsonString);
        JSONArray verifiedDevices = jsonData.getJSONArray("verified_devices");

        // ডিভাইস আইডি (এইখানে Build.SERIAL আপনি নিজের ডিভাইসের সিরিয়াল নম্বর দিয়ে চেক করবেন)
        String deviceID = "c41e398485531f31"; // উদাহরণ স্বরূপ একটি ডিভাইস আইডি

        // যাচাই করা
        boolean isVerified = false;
        for (int i = 0; i < verifiedDevices.length(); i++) {
            if (verifiedDevices.getString(i).equals(deviceID)) {
                isVerified = true;
                break;
            }
        }

        // ফলাফল দেখানো
        if (isVerified) {
            showMessage("Device Verified!");
        } else {
            showMessage("This Device is Not Verified!");
        }
    }

    // মেসেজ দেখানোর জন্য একটি সহায়ক ফাংশন
    private static void showMessage(String message) {
        System.out.println(message);
    }
}