package com.android.nfc;

import android.os.RemoteException;

import android.app.Activity;
import android.content.ActivityNotFoundException;
import android.content.Intent;
import android.os.Bundle;
import android.widget.TextView;
import android.view.View;
import android.util.Log;
import com.android.nfc.nxp.NativeP2pDevice;
import android.os.AsyncTask;
import android.widget.Toast;
import android.content.Context;

public class NfcTrigger extends Activity {
	static final String TAG = "NfcTrigger";
	private Integer in = 0;
	protected NfcService app;	


    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.trigger);
        TextView text = (TextView)findViewById(R.id.text);
        app = (NfcService)getApplication();
        
    }
    
    public void NfcOn(View view) {
    	Log.i(TAG, "NfcOn");
    	in = 1;    	
    	new NfcEnableDisable().execute(in);
    	//app.onLlcpLinkActivated(new NativeP2pDevice());    	
    }
    
    public void NfcOff(View view) {
    	Log.i(TAG, "NfcOff");
    	in = 2;    	
    	new NfcEnableDisable().execute(in);
    	//app.onLlcpLinkDeactivated(new NativeP2pDevice()); 
    }

    public void NfcONOFF(View view) {
	in = 2;    	
    	new NfcEnableDisable().execute(in);
	Log.i(TAG, "NfcOff");
    
    	in = 1;    	
    	new NfcEnableDisable().execute(in);
	Log.i(TAG, "NfcOn");

    	//app.onLlcpLinkDeactivated(new NativeP2pDevice()); 
    }
    
    private class NfcEnableDisable extends AsyncTask<Integer, Void, String> {
    	@Override
    	protected void onPreExecute() {
    		Log.i(TAG, "Forcing NFC");
    		Toast.makeText(NfcTrigger.this, "Forcing NFC", Toast.LENGTH_SHORT).show();
    		
    	}
    	
    	@Override   	
    	protected String doInBackground(Integer... i) {
		
		if (i[0] == 1) {    		
			try {
				Thread.sleep(10000);
			} catch (InterruptedException e) {
				// TODO Auto-generated catch block
				e.printStackTrace();
			}
		}
    		if(i[0] == 1){    			
    			app.onLlcpLinkActivated(new NativeP2pDevice());    			
    		}
    		
    		if(i[0] == 2){    			
    			app.onLlcpLinkDeactivated(new NativeP2pDevice());
    		}   		
    		return "Forcing Finished";
    	}	
    	   	
    	@Override
    	protected void onPostExecute(String s){
    		Log.i(TAG, "Forcing Finished");
    		Toast.makeText(NfcTrigger.this, s, Toast.LENGTH_SHORT).show();
    		
    	}
    	
    }

}
