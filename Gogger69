--  ____        _       _    _       _      
-- |  _ \      | |     | |  | |     | |    
-- | |_) |_   _| |_ ___| |__| |_   _| |__  
-- |  _ <| | | | __/ _ \  __  | | | | '_ \ 
-- | |_) | |_| | ||  __/ |  | | |_| | |_) |
-- |____/ \__, |\__\___|_|  |_|\__,_|_.__/ 
--         __/ |                           
--        |___/          

-- Protected by ByteHub AES
local 1kbBa688 = 5013 
local LSqCsCYK = 5371 
local MIZkZuj5 = 3643 
function 9A7xCoVD() return 8 end 

local base64 = {
    _chars = 'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/',
    decode = function(data)
        local b = base64._chars
        data = string.gsub(data, '[^' .. b .. '=]', '')
        return (data:gsub('.', function(x)
            if x == '=' then return '' end
            local r,f='',(b:find(x)-1)
            for i=6,1,-1 do r = r .. (f%2^i - f%2^(i-1) > 0 and '1' or '0') end
            return r
        end):gsub('%d%d%d%d%d%d%d%d', function(x)
            local c=0
            for i=1,8 do c = c + (x:sub(i,i) == '1' and 2^(8 - i) or 0) end
            return string.char(c)
        end))
    end
}

local function concat_bytes(parts)
    local res = ""
    for _, p in ipairs(parts) do
        res = res .. base64.decode(p)
    end
    return res
end

local key_parts = {
    "ky8s+w==",
    "Dmmlww==",
    "VPwFKw==",
    "3oZ/fA==",
}

local iv_parts = {
    "8vD4bQ==",
    "cY20kw==",
    "DJExRQ==",
    "KzzSYg==",
}

local key = concat_bytes(key_parts)
local iv = concat_bytes(iv_parts)

local encrypted_b64 = "2kWrEXWyzgM="
local encrypted = base64.decode(encrypted_b64)


local function xor_decrypt(data, key)
    local res = {}
    for i = 1, #data do
        local c = string.byte(data, i)
        local k = string.byte(key, (i - 1) % #key + 1)
        res[i] = string.char(bit32.bxor(c, k))
    end
    return table.concat(res)
end

local decrypted_compressed = xor_decrypt(encrypted, key)

local zlib = require("zlib")
local ok, decompressed = pcall(zlib.inflate(), decrypted_compressed)
if not ok then
    error("Failed to decompress code")
end

assert(load(decompressed))()
