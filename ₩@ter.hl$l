Shader "Custom/WaterShader2D" {
    Properties {
        _MainTex ("Texture", 2D) = "white" {}
        _WaveAmplitude ("Wave Amplitude", Range(0, 1)) = 0.1
        _WaveSpeed ("Wave Speed", Range(0, 10)) = 1
    }

    SubShader {
        Tags {"Queue"="Transparent" "RenderType"="Transparent"}
        LOD 100

        CGPROGRAM
        #pragma surface surf Lambert

        sampler2D _MainTex;
        float _WaveAmplitude;
        float _WaveSpeed;

        struct Input {
            float2 uv_MainTex;
        };

        void surf (Input IN, inout SurfaceOutput o) {
            float2 uv = IN.uv_MainTex;
            uv.y += _WaveAmplitude * sin((_WaveSpeed * uv.x + _Time.y));
            o.Albedo = tex2D(_MainTex, uv).rgb;
            o.Alpha = tex2D(_MainTex, uv).a;
        }
        ENDCG
    }
    FallBack "Diffuse"
}
